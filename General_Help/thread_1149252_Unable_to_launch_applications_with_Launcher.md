---
title: "Unable to launch applications with Launcher"
date: 2009-05-05
forum: General Help
---

### Post by funonline41 on 2009-05-05
Hi - I am new to Linux and Ubuntu. I hae Ubuntu 8.04 on my Dell laptop. I am trying to create Launchers on my desktop. As an example I tried to get a launcher for Aptitude application that I recently download and am able to get running using command line.
When executing the launcher I get the error "There was an error launching the application:
Details: Failed to execute child process "Aptitude" No such file or directory"
 
But yet I can run command line from any directory and get Aptitude to run. I had the same problem when I tried this with Gedit. So what am I doing wrong?
 
On my command line I simply have written : Aptitude
Under permissions I have the checkmark to execute file as a program.
 
Thanks if anyone can help.

---

### Post by funonline41 on 2009-05-05
Ok - It appears part of the problem was with the capitol "A" ain Aptitude. So now that gets rid of the error message. So now the command line is : aptitude,
I no longer get the error message but nothing happens. I click on the Launcher icon and absolutely nothing.
 
I also have tried /usr/bin/aptitude     and  /user/bin/aptitude --desktop   
but no success. However at lease I have fixed the error message.

---

### Post by geirha on 2009-05-05
aptitude does not have a gui, so it needs to be run in a terminal. In the launcher's properties you need to set the type to "Application in terminal" instead of "Application".

---

### Post by funonline41 on 2009-05-06
Geirha - You are worth your weight in gold!!!  Thanks it works. You guys are so helpful to us beginners :)
 
Kirk

---

