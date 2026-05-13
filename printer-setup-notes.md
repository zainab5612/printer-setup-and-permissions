[printer setup, NTFS, printer cloud (1).pdf](https://github.com/user-attachments/files/27719847/printer.setup.NTFS.printer.cloud.1.pdf)


Printer setup+


➔ On Server Manager, go to Manage 
➔ Add Roles and Features Wizard 
➔ Under Server Roles, check:
  - Print and Document Services 
  - DHCP Server
---

1. Adding a printer using DHCP

➔ Tools → DHCP 
➔ Server name → IPv4 → right click → New Scope 
➔ Set up IP address range (DHCP range) 
➔ Lease duration can stay default 
➔ Default gateway (router) 
➔ DNS: enter domain name and DNS server IP



<img width="516" height="429" alt="Screenshot 2026-05-11 213917" src="https://github.com/user-attachments/assets/08a82c40-9738-4de6-b848-96cf2dc3cf8e" />

<img width="523" height="441" alt="Screenshot 2026-05-11 214237" src="https://github.com/user-attachments/assets/9eb9d369-9afb-4976-979b-3429a72363a7" />



---

Testing DHCP

➔ Test if users receive an IP address within the configured range 

Issue:
➔ Client received 169.254.x.x 

Cause:
➔ DHCP server was not authorized 

Fix:
➔ Authorized DHCP in Active Directory 

Result:
➔ Client received correct IP from DHCP 

----

Adding a Printer

➔ Tools → Print Management 
➔ Print Server → Server Name → Printers 
➔ Right click → Add Printer 

➔ Choose:
  Add an IPP, TCP/IP, or Web Services printer by IP or hostname 

➔ Device type: TCP/IP 
➔ IP address: 192.168.10.50 
➔ It may fail — that’s OK — continue 
➔ Use Generic driver (Generic / Text Only) 

<img width="579" height="438" alt="Screenshot 2026-05-11 232413" src="https://github.com/user-attachments/assets/6248ae5d-38c5-42f4-913f-98eabffb36a3" />

<img width="574" height="434" alt="Screenshot 2026-05-11 233019" src="https://github.com/user-attachments/assets/e4174c73-5f63-4318-9f48-f27a02c9efd3" />


---


Testing on User Side (Windows 11)

➔ Press Win + R 
➔ Enter:
  \\192.168.10.10 
  or 
  \\CA-SD-01 
Can also be checked on control panel —-- devices and printers

➔ This is the network path to the server 

➔ You should see the printer name 

<img width="682" height="276" alt="Screenshot 2026-05-11 234035" src="https://github.com/user-attachments/assets/5905df0d-5e4f-43b5-9949-f8c31c4457db" />


➔ Print Management → Add a new printer 
➔ Add a printer using an existing port 
➔ Install a new driver 

➔ Choose HP (if available) 
  If not → use Windows Update 

➔ Uncheck “Share this printer” 

<img width="577" height="431" alt="Screenshot 2026-05-12 183308" src="https://github.com/user-attachments/assets/5e196498-7a91-4462-96ae-8b0cf2e6af79" />

----

Setting Permissions (Security)

➔ Right click printer → Properties 
➔ Security → Advanced → Add → Select Principal 
➔ Search for group (example: "tech") → Check Names 

<img width="472" height="313" alt="Screenshot 2026-05-12 184059" src="https://github.com/user-attachments/assets/1d34b27b-9919-41ba-852b-27be413c210a" />


----

Testing Permissions

➔ Log in as user (Windows 11) 
➔ Go to:
  Control Panel → Devices and Printers 
  OR 
  Settings → Printers & Scanners 

➔ Verify that users in the "tech" group can access the printer 

<img width="681" height="339" alt="Screenshot 2026-05-12 184557" src="https://github.com/user-attachments/assets/c0a63e04-c19a-4a44-99b6-25634b42fca3" />


---

Troubleshooting Printers

➔ If driver issues occur → change the driver 

➔ Printer Properties → Advanced → New Driver 
➔ Use “Have Disk” to install correct manufacturer driver 

➔ Re-share the printer and list it in the directory 

➔ User may need to:
  - Restart 
  - Reinstall the printer on their machine 
<img width="567" height="409" alt="Screenshot 2026-05-12 185257" src="https://github.com/user-attachments/assets/1a1128ea-bcbd-4949-b897-a8dc1b8fb4fc" />
---



