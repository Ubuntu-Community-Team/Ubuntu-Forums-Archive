---
title: "How to that Windows Admins and Developers May find useful"
date: 2009-04-28
forum: General Help
---

### Post by amadeus266 on 2009-04-28
As the title implies, this How To is for windows Admins. Please note before you decide to bash me for posting this in a Linux forum, I accomplished this task with Ubuntu 8.04. What I have done here, I have determined through many, many hours of searching, has NEVER been tried before. This was necessary in my case to compensate for roaming employees when roaming profiles would not achieve what I needed. So here goes my first How To...

How to set a user variable on server when connecting through RDP

I needed a variable set on the windows server so that when a user logs in from a given terminal and only allow a single application to run and my server would know which terminal they were using by checking the variable. This was not an easy affair! This is how I did it.
Note: If you go to Start->My Computer-> Manage-> Advanced, Environment Variables on the server, you will not see a user# variable even after these steps.
Step 1: On the server I created a folder and named it “test”
Step 2: in the folder create a text document and name it “userinfo1,bat”. This file will tell the server to store the variable for this user.
Step 3: open userinfo1.bat for editing in notepad
	Add the following:
				&echo off
				set user#=1
				start notepad <-----replace notepad with name of application
	save the file.
Step 4: On the 1st workstation open Remote Desktop Connection (or Terminal Server Client in Ubuntu)
Step 5: In remote desktop connection use the following settings:
	-fill in the username and password fields if desired
	-connect to server "Server" <---replace with the server's name or ip 
	-on the Programs tab click Start the following on connection
	-in the "Program path" box, enter c:\test\userinfo1.bat
        -in the "Start in the following folder" box, enter the path to the application's directory
Step 6: save the connection information on the desktop
Step 7: double-click the new icon on the desktop and start the connection
Step 8: You should now see the server login screen, Log on.
Step 9: Repeat this process on every terminal incrementing the number in the batch file by the terminal id number (userinfo1.bat, userinfo2.bat, etc.)

Now when your application needs to know which terminal your user is running, it can look up that variable.:popcorn:

---

