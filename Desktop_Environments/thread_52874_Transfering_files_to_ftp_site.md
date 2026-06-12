---
title: "Transfering files to ftp site"
date: 2005-07-29
forum: Desktop Environments
---

### Post by Irony on 2005-07-29
In Windows if I want to update my website I simply open up the ftp section in the browser then drag the contents of my computer mirror site into the browser window.

In ubuntu I can open up the ftp site the same as in windows but if I drag a jpeg image over it simply opens up the image in firefox - how do I transfer files from my computer into my ftp site?

Looking at the forums it looks like I need to install gftp? However there is a common version and a gtk version, what does this actually mean?

---

### Post by Zelut on 2005-07-29
I use gftp to update my two sites.  Simple as #sudo apt-get install gftp.  It'll show up on your Internet menu on the panel.  Really simple to use.

---

### Post by Irony on 2005-07-29
Thanks its worked, I've just transferred a file.

I'm still getting used to the *sudo apt-get install* instruction. When I did *sudo apt-get install gftp* it installed the 4 options shown in synaptic. People seem to use sudo apt-get install more than synaptic. It also seems strange to me that the programs that ubuntu uses seem to come mostly from repositories whereas in windows I used to get them from all over.

---

### Post by shakin on 2005-07-29
[QUOTE=Irony]Thanks its worked, I've just transferred a file.

I'm still getting used to the *sudo apt-get install* instruction. When I did *sudo apt-get install gftp* it installed the 4 options shown in synaptic. People seem to use sudo apt-get install more than synaptic. It also seems strange to me that the programs that ubuntu uses seem to come mostly from repositories whereas in windows I used to get them from all over.[/QUOTE]

'sudo apt-get install' is easier when telling people what to do since they can simply copy and paste it. Most people use Synaptic for everyday use.

Repositories are essentially a side effect of having multiple distros that don't standardize on package management or libraries, etc. It's a place to get programs you know for sure will run on Ubuntu with minimal fuss.

BTW, from the places menu you can select "Connect to Server" and select FTP as a type (among others). If it's an FTP you will use often, doing this will place it in the Places menu so you can use it just like a local folder. KDE has something similar called Network Folders.

---

### Post by Zelut on 2005-07-29
apt-get or Synaptic are both great ways to install programs.  I think a lot of more advanced users are just used to using the terminal for commands (I think its faster) so that is why I suggest apt-get but Synaptic will do the same thing.

Yeah, the linux communities put together packages of popular & essential files in repositories so that everyone has access, everyone (for the most part) is on the same level.  That way it helps in troubleshooting & things like that.  You'll get used to how things are different before too long.

It is hard to get used to an entirely new OS-world... but you'll enjoy it :)

---

### Post by Irony on 2005-07-29
Thanks for replies.

It still amazes me that all this stuff (open office, gimp, blender, etc) is free, I was expecting linux to be a bit 'clunky' but it seems as professional as windows but I'm not tied to expensive licences for each computer. Ubuntu even sent me a bunch of discs, install as well as Live!!

---

### Post by BanskuZ on 2005-07-29
[QUOTE=Irony]Thanks for replies.

It still amazes me that all this stuff (open office, gimp, blender, etc) is free, I was expecting linux to be a bit 'clunky' but it seems as professional as windows but I'm not tied to expensive licences for each computer. **Ubuntu even sent me a bunch of discs**, install as well as Live!![/QUOTE]

Where they get money? Hosting this forum, packages and ubuntu isos eats a lot of bandwith. And sending free discs eat a lot of money too.

---

### Post by vimme on 2005-08-15
I have problem with Gftp, hope that someone can help me.

When I transfer a picture to my site, it doesn't show up, it's name shows but image doesn't. And when browsing in Gftp all the other .jpg files that were there prior has different icon, with Gftp all the trasfers has plug-like icon.

So am I doing something wrong here or is it just the settings?

---

