---
title: "How to gain permission to var/www?"
date: 2009-09-26
forum: Desktop Environments
---

### Post by rkylain24 on 2009-09-26
I recently installed the ubuntu 9.04 desktop version on a imac g3. I installed apache2 hoping to be able to host a simple website I am currently working on. When I try to copy files into var/www/ it says i do not have permission for var/www/. I tried a chmod command but it sais i didn't have permission to change it. I'm really lost here and i have a general knowledge of the terminal, but not enough. How can I gain permission to copy my website (html, pdf, and jpeg) files into the var/www/? I have heard that this is not very secure, but i really don't use the computer much, and i don't have any vital information on the computer. I just want to be able to use the GUI to copy the files from my flash drive into var/www/. Then i would be able to view the website from any computer providing i know the IP of the computer hosting the site right? Well thats what i want to happen. Maybe idk what i'm talking about, but I am really having problems and no other posts seem to answer the question. Thanks in advance.

-Ryan

---

### Post by andrea000 on 2009-09-26
Have you tried this

> sudo chmod 755 -R /var/www/

---

### Post by argen3ng33k on 2009-09-27
I had a similar problem with my own website. Make sure that the www-data group has the right permissions.

as long as you have the IP of the computer/server you are trying to acces and the right credentials you can go to

places > connect to server > (choose option) to connect to the server to drop the files that you need, you can even create a bookmark for easy access once you know how you would like to connect and that you connect successfully.

---

### Post by mcduck on 2009-09-27
> **rkylain24 said:**
> I recently installed the ubuntu 9.04 desktop version on a imac g3. I installed apache2 hoping to be able to host a simple website I am currently working on. When I try to copy files into var/www/ it says i do not have permission for var/www/. I tried a chmod command but it sais i didn't have permission to change it. I'm really lost here and i have a general knowledge of the terminal, but not enough. How can I gain permission to copy my website (html, pdf, and jpeg) files into the var/www/? I have heard that this is not very secure, but i really don't use the computer much, and i don't have any vital information on the computer. I just want to be able to use the GUI to copy the files from my flash drive into var/www/. Then i would be able to view the website from any computer providing i know the IP of the computer hosting the site right? Well thats what i want to happen. Maybe idk what i'm talking about, but I am really having problems and no other posts seem to answer the question. Thanks in advance.

-Ryan

The safe way is to not change the permissions of the /var/www directory, but to change *your* permisssions. Ubuntu allows admin users to gain temporary root permissions by using "sudo", so that's what you need to do.

First read this: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")
(it also explains why you couldn't just chmod the directory)

Then, open a terminal and run "gksudo nautilus" to open the file manager with root permissions, and use that to move your files into /var/www. :)

If you need to do this often, the common way is to change the ownership of the /var/www directory to "www-data" or some similar group, and then add your user to that group. This would allow you to have write permissions into that directory without having to use "sudo" or compromising your server's security by allowing everybody to write into that directory.

---

### Post by rkylain24 on 2009-09-27
'gksudo nautilus' did exactly what i needed. Thank you very much mcduck i knew there had to be an easy way to do it. Now i ran into another problem. When i try to acces the website from another computer i enter "http://???.??.???.??/ into the web browser and i get "Forbidden. You don't have permission to access /index.html on this server. Then it says the apache version and the IP and port 80. I'm hoping that this is a simple edit to one of the files in /ect/apache2/ but i don't know which one, or what to change. Again Thanks in advance.

---

### Post by mcduck on 2009-09-27
> **rkylain24 said:**
> 'gksudo nautilus' did exactly what i needed. Thank you very much mcduck i knew there had to be an easy way to do it. Now i ran into another problem. When i try to acces the website from another computer i enter "http://???.??.???.??/ into the web browser and i get "Forbidden. You don't have permission to access /index.html on this server. Then it says the apache version and the IP and port 80. I'm hoping that this is a simple edit to one of the files in /ect/apache2/ but i don't know which one, or what to change. Again Thanks in advance.

Check the permissions of the files you put into /var/www, since you are copying them from a flash drive (that probably uses FAT as it's filesystem) the file permissions might not be correct.

The files should have 644 permissions (rw-r--r--) and directories 755 (rwxr-xr-x).

---

### Post by rkylain24 on 2009-09-27
Well the ls -l command was saying  I didn't have permission so I just did the gksudo nautilus and then changed the permissions tab in properties of the folder I put inside the www folder. It works great now. One day i'll try tackeling how to get ftp access with a password and stuff, but this is all i care to do for now. Especially since that computer doesn't have internet access very much because I need a 4 port hub.

---

