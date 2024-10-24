
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites, Setup, and Installation</h1>
This guide details the necessary requirements and steps for installing osTicket, an open-source help desk ticketing system.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> 

<h2>List of Prerequisites</h2>

- IIS
- PHP Manager
- VC_redistx86
- MySQL 5.5.62
- Rewrite Module
- Heidi SQL

<h2>Installation Steps</h2>

<p>
</p>
<p>
<h3>&#9312; Create a Virtual Machine on Azure</h3>
The first step is to create a virtual machine on Azure. 
Choose the image or base operating machine as Windows 10 Pro, version 22H2.</p>
<p>
<img width="758" alt="VM setup-windows 10" src="https://i.imgur.com/zdx9hfQ.png">

<p>
</p>
<p>
<strong> NOTE: Make sure to set the size to at least 2 vcpus and 16 GiB memory. 
And confirm that RDP (3389) is allowed in "Select inbound ports" in order to allow Remote Desktop access to the VM.</strong> </p>
<p>
<img width="757" alt="VM inbound ports" src="https://i.imgur.com/XxOAcpx.png">



</p>
<br />

<p>
</p>
<p>
<h3>&#9313; Review and Create </h3>
<p>Click on the last check box to confirm an eligible Windows 10 license then proceed to "Review + create". A validation process will occur then once it has passed simply continue to create.</p>

</p>
<br>
<h3>&#9314; Find your VM's public IP address</h3>
<p></p>Allow some time for your deployment to complete then find your VM's public IP address and copy it.</p>
<p>
<img width="1009" alt="VM IP ADDRESS" src="https://i.imgur.com/DsKtMlO.png">


</p>
<p>
<h3>&#9315; Connect to your VM using the Remote Desktop Connection app</h3>
<p>Open your Remote Desktop Connection app and paste the VM's IP and login with the same login credentials used to create the VM.</p>
<p>
<img width="302" alt="Remote desktop app" src="https://i.imgur.com/ii4Gxkk.png">


</p>
<br />
<h3>&#9316; Enable IIS </h3>
<p> Once the VM is open, we will have to install / enable IIS. Go to the Control Panel and open the programs applet. Under programs, select "Turn Windows features on or off".</p>
<p> <img width="552" alt="CONTROL PANEL PROGRAMS" src="https://i.imgur.com/AxyCjlE.png">

  
</p>
<p>Then you will have to enable and expand the following features:</p>
<p><img width="295" alt="Checklist 2" src="https://i.imgur.com/V7MSA5p.png">
</p>
<p> [X] Internet Information Services</p>
<p>[X] Web Management Tools </p>
<p>[X] IIS Management Console </p>
<p>[X] World Wide Web Services  </p>
<p>[X] Application Development Features </p>
<p>[X] CGI</p>
<p>[X] Common HTTP Features</p>
<br>
<p> Click okay and the features should be enabled.</p>
<br>
<p> <strong> NOTE: To quickly test if the changes were applied succesfully, simply type 127.0.0.1 on your browser and the page below should appear. </strong></p>
<img width="1094" alt="WINDOWS IIS" src="https://i.imgur.com/gSXraX5.png">
<br> <br>
<h3>&#9317; Download and Install PHP Manager</h3>
<p> Simply download and install PHP manager from the <a href="https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6"> installation files </a>(PHPManagerForIIS_V1.5.0.msi) 
</p> <br>
<p><img width="386" alt="PHP Manager" src="https://i.imgur.com/mohWcn7.png">
</p> 
<br>
<h3>&#9318; Download and Install the Rewrite Module</h3>
<p> Download and install the rewrite module (rewrite_amd64_en-US.msi) from the <a href="https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6"> installation files </a> </p>
<p><img width="386" alt="rewrite module" src="https://i.imgur.com/NAzd4XN.png"></p>
<h3>&#9319; Create a new directory</h3>
<p>Proceed to File Explorer and create the directory C:\PHP </p>
<img width="647" alt="PHP" src="https://i.imgur.com/Y4QPGqj.png">
<br>
<br>
<h3>&#9320; Download and install php-7.3.8-nts-Win32-VC15-x86.zip </h3>
<p> Download and install php-7.3.8-nts-Win32-VC15-x86.zip from the <a href="https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6"> installation files </a> and unzip the contents into the newly created C:\PHP </p>
<img width="631" alt="PHP zip" src="https://i.imgur.com/gtFHjCr.png">
<br>
<h3>&#9321; Download and install VC_redist.x86.exe </h3>
<img width="631" alt="PHP zip" src="https://i.imgur.com/1okUnXa.png">
<br>
<h3>&#9322; Download and install MySQL 5.5.62 </h3>
<p> Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi) from the <a href="https://drive.google.com/drive/u/2/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6"> installation files </a>  and select the following configurations; </p>
<p> [X] Typical Setup</p>
<p>[X] Launch Configuration Wizard after install </p>
<p>[X]Standard Configuration 
</p>
<br>
<img width="383" alt="mysql" src="https://i.imgur.com/zY7L1TB.png">
<br>
<h3>&#9323; Launch IIS as an administrator</h3>
<p> Search for IIS in the windows search bar and right click it and select open as administrator</p>
<br>
<h3>&#9324; Register PHP Manager </h3>
<br>
<img width="682" alt="PHP registration 2" src="https://i.imgur.com/FZeOyNl.png">

<br>
<br>
<p><strong> NOTE: Registration will require you to provide a path to "php-cgie.exe". Simply lead it to the PHP folder previously created and you will find the file it is asking for. 
</strong></p>
<br>
<img width="623" alt="PHP path " src="https://i.imgur.com/I2ETZWQ.png">

<br>
<p>
</p> 
<h3>&#9325; Restart the IIS server</h3>
<p> The restart button can be found on the right side of the window.</p>
<br>
<img width="623" alt="Restart IIS" src="https://i.imgur.com/ee7miH5.png">
<br>
<br>
<h3>&#9326; Download and install osTicket</h3>
<p> Download and install osTicket v1.15.8 from the installation files and extract the contents to c:\inetpub\wwwroot </p>
<br>
<img width="547" alt="inetpub" src="https://i.imgur.com/vMRBLB5.png">
<p> Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”</p>
<br>
<br>
<h3>&#9327; Restart the IIS server again.</h3>
<img width="623" alt="Restart IIS" src="https://i.imgur.com/ee7miH5.png">
<br>
<br>
<h3>&#9328; Launch osTicket </h3>
<p>On the left hand side of IIS, Expand on the VM name -> Sites - > Default Website -> osTicket </p>
<img width="623" alt="osTicket" src="https://i.imgur.com/atosLwZ.png">
<p></p>
<p><strong>NOTE: Make sure to click on osTicket</strong></p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>
<h3>&#9329; Click on Browse *80 to launch osTicket</h3>
<p> On the right side of the window, click on browse *80 </p>
<img width="623" alt="browse80" src="https://i.imgur.com/YydEwxj.png">
<br>
<br>
<br>
<p><strong>This should then lead to your browser opening osTicket</strong>.</p>
<br>
<br>
<img width="664" alt="osTicket browser" src="https://i.imgur.com/vrQPPPg.png">
<br>
<br>
<br>
<h3>&#9330; Enable extensions</h3>
<p>Open IIS and click on PHP Manager and select "enable or disable extension". </p>\
<img width="664" alt="PHP manager" src="https://i.imgur.com/ebZevK0.png">
<p>Enable the following extensions:</p>
<p>[X]Enable: php_imap.dll</p>
<p>[X]Enable: php_intl.dll</p>
<p>[X]Enable: php_opcache.dll</p>
<img width="273" alt="php enable 2" src="https://i.imgur.com/LbrUd94.png">
<br>
<br>
<br>
<h3>&#9331; Refresh osTicket</h3>

<p>Refresh the osTicket page on the browser and notice some extensions will now appear active.</p>
<img width="608" alt="OSticket changes" src="https://i.imgur.com/lhRn53r.png">
<br>
<br>
<br>

<h3>&#12881; Rename ost-config.ph</h3>

<p> Under C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php, rename "ost-sampleconfig.ph" to "ost-config.ph"</p>
<img width="527" alt="ostconfig rename" src="https://i.imgur.com/vmBsm4n.png">
<br>
<br>
<br>

<h3>&#12882; Change ost-config.ph permissions</h3>

<p>Change ost-config.php permissions by right clicking and selecting</p>
<p>Properties -> Security -> Advance -> Disable inheritance</p> 
<p>Select remove all inherited permissions and add everyone as a principal. Select all boxes to ensure all permissions are granted. </p>
<img width="571" alt="Permissions" src="https://i.imgur.com/0rWhZud.png">
<p><strong>.</strong></p>
<p><strong>.</strong></p>

<h3>&#12883; Continue osTicket installation</h3>

<p> Continue the osTicket installer on your browser by filling the first half of the page.</p>
<img width="611" alt="osticket signup" src="https://i.imgur.com/gYSXMrq.png">
<br>
<br>
<p><strong>NOTE: Don't worry about the database credentials. We'll fill those out later.</strong> </p>
<br>
<p><strong>.</strong></p>
<p><strong>.</strong></p>

<h3>&#12884; Download and install Heidi SQL from the installation files</h3>

<p>Open Heidi SQL and create a new session. Make sure to fill in the username as root and create a password. After filling up your credentials now click open and a new session should show up.
</p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>
<p><strong>.</strong></p>

<h3>&#12885; Create new database </h3>

<p>On the left side of the window, right click on "Unnamed" and click create new database and name it "osTicket".</p>
<img width="512" alt="SQL" src="https://i.imgur.com/JoC59EA.png">
<img width="512" alt="SQL" src="https://i.imgur.com/tXLbJZe.png">
<br>
<br>
<p><strong>.</strong></p>
<p><strong>.</strong></p>

<h3>&#12886; Finish signing up</h3>

<p>Then go back to your osTicket browser and fill up the missing credentials. 
It should look something like this.</p>
<img width="308" alt="osticket final signup" src="https://i.imgur.com/QxT9aNp.png">
<p><strong>.</strong></p>
<p><strong>.</strong></p>

<h3>&#12887; Finalize osTicket installation</h3>

<p>Click install and osTicket should begin setting up. </p>
<img width="308" alt="osticket final signup" src="https://i.imgur.com/6rpQPFM.png">
<p><strong>.</strong></p>
<p><strong>.</strong></p>

<h2> Final cleanup steps</h2>
<p>[X] Delete "setup" file located at C:\inetpub\wwwroot\osTicket\setup</p>
<p>[X] Set permissions of "ost-config.php" to read only.</p>
<p> File is located at C:\inetpub\wwwroot\osTicket\include\ost-config.php</p>
<br>
<br>
<h1>Congratulations!!! &#127881; you just installed osTicket</h1>
