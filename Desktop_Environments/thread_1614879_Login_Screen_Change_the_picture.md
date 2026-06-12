---
title: "Login Screen Change the picture"
date: 2010-11-06
forum: Desktop Environments
---

### Post by NoSuchDevice on 2010-11-06
Hello All, 

I recently got this theme / login screen from here > [http://art.gnome.org/themes/gdm_greeter](http://art.gnome.org/themes/gdm_greeter)

It is the 3rd one named "Login-Scan-fusion" I don't know how to set this up, how do I make it my login screen? I am using ubuntu 10.4LTS

Thanks
NoSuchDevice

---

### Post by 4ll41 on 2010-11-06
[FONT=Verdana]These steps did the job for me in Lucid. In a terminal:

	   $ [/FONT][B][FONT=Verdana]sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow && exit

[/FONT][/B][FONT=Verdana]Then logout, when you do, a window will appear at the login screen where you can set your login screen. Select your photo
 and log back in. When you do, open up another terminal and type:[/FONT][FONT=Verdana] 	   $ **sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop**[/FONT]

---

### Post by NoSuchDevice on 2010-11-06
OK I am trying to get the folder to go in usr/share/backgrounds but I can't how do I give my self permissions?

Thanks

---

### Post by NoSuchDevice on 2010-11-06
OK I found out how do give my self permissions, from that link on top I downloaded the "loginScanFusion.tar.gz" I want that whole thing to be my login screen theme. I checked some websites and It says under** System>Administration>Login Window**.

I don't have the login window, I got "login screen" (which only changes the behaviour not theme)...I am using ubuntu 10.4LTS please help 

Thanks

---

### Post by 4ll41 on 2010-11-07
I am not quite sure what you are trying to do. Have you tried to do it the way I told you and it didn't work?

---

