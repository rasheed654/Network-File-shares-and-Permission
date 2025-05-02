
<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Step 1 Create some action files with various permissions
- Step 2 Attempt to access file shares as a normal user
- Step 3
- Step 4

<h2>Create some action files with various permissions</h2>
<img width="439" alt="image" src="https://github.com/user-attachments/assets/f9a0a5ab-9334-437d-af30-e0bdfef2395a" />
<p>Connect/log into DC-1 as your domain admin account (mydomain.com\jane_admin)</p>
<img width="439" alt="image" src="https://github.com/user-attachments/assets/dde6adb7-dab2-4543-b6b3-754eb93f744c" />
<p>Connect/log into Client-1 as a normal user (mydomain\<someuser>)</p>
<img width="1129" alt="image" src="https://github.com/user-attachments/assets/8119b8b7-19d2-4034-9703-cf40cc71859a" />
<p>Open file explorer->This Pc->Windows C Drive</p>
<img width="1131" alt="image" src="https://github.com/user-attachments/assets/7b8d9b38-0a84-4705-a27e-634d86c523d2" />
<p>On DC-1, on the C:\ drive, create 4 folders: “read-access”, “write-access”, “no-access”, “accounting”</p>
<img width="1122" alt="Screenshot 2025-05-02 at 1 37 12 PM" src="https://github.com/user-attachments/assets/a5b3cc0b-9830-41fc-abaa-e367625b9474" />
<p>Right click and Go to Properties</p>
<img width="363" alt="image" src="https://github.com/user-attachments/assets/151775b3-7030-46c0-9017-dd3af257f506" />
<p>Go to Sharing and then click on share</p>
<img width="610" alt="image" src="https://github.com/user-attachments/assets/393ee310-fd6b-4509-8187-e6a790b90fe4" />
<p>Type in Domain Users and click Add</p>
<img width="611" alt="image" src="https://github.com/user-attachments/assets/681ad190-72f1-4a91-aa14-c1c399ff4730" />
<p>Make sure Read access is selected </p>
<img width="1128" alt="image" src="https://github.com/user-attachments/assets/5d292bcd-bf50-426e-ad0a-26f78e2e449e" />
<p>Right click on wite access and then click properties. click on sharing and then share</p>
  <img width="1124" alt="Screenshot 2025-05-02 at 1 52 53 PM" src="https://github.com/user-attachments/assets/99bb9e96-3f6f-4ee3-8b06-2abd07f62c91" />
<p>Add domainusers and make sure Permission level is on read/write</p>
  <img width="1129" alt="Screenshot 2025-05-02 at 1 55 34 PM" src="https://github.com/user-attachments/assets/2e9cf013-961a-47ff-8b09-73879dee1be8" />

<p>Folder: “no-access”, Group: “Domain Admins”, “Permissions: “Read/Write”</p>

<h2>Attempt to access file shares as a normal user</h2>
<img width="1125" alt="image" src="https://github.com/user-attachments/assets/774bb483-6895-481b-b80b-18a10839c3d0" />

<p>Login to client-1 as a normal user, open file explorer and type in \\dc-1 to see the no-access, read access and write-access folders</p>




