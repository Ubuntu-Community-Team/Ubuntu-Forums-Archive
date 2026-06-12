---
title: "Samba setup to share with Winxp without manual editing?"
date: 2005-10-18
forum: Desktop Environments
---

### Post by jetpeach on 2005-10-18
I have read through a number of the threads here and I'm just getting more confused.  I tried to install SWAT because I thought this was going to be graphical and easy, but I don't know how to run SWAT and now I read threads about needing to run as root and other problems and people saying SWAT is crummy anyway.
My goal is to have my WinXP machine access my Ubuntu machine, it sounds pretty darn simple.  But it seems there is no way to do this using GUI interfaces and without editing smbconfig files and junk?  If anyone can show me a way, I would greatly appreciate it.
As of now, I'm chosen "share folder" in Gnome, chosen to share with SMB, named the share, and checked the "Allow browsing folder" box.  Under general Windows sharing settings, I left the defaults.  Using synaptic, I installed SWAT, but it seems I can't run it.
From here, can someone outline exactly what I need to do to get this to work?  I know it has been done before, but all the threads turn into smbconfig editing festivals and I already tried editing my config files in Hoary without any luck, so I'm hoping to be able to install a program or use some other configuration tool, or run a script that will set me up from here.
Thanks,
Jet

---

### Post by jonesy on 2005-10-18
SWAT is a web-base application that requires you to connect to a specific port on your computer with your web browser to configure it.  Sometimes this needs to be enabled through xinetd though I haven't done this on ubuntu or any other debian based system and since i don't have it installed I can't help you right now.

Short of that, the smb.conf file isn't terribly complicated.  Most of the defaults are fine, just setup the hostname and exports.  Lastly, you need to add users who have permission to access the shares.  This is done through smbpasswd.  You need to add users with smbpasswd -a <user> and then enable them using smbpasswd -e <user>.

---

### Post by wjp.reg on 2005-10-18
jetpeach;

I'd like to suggest a few things, keeping in mind I'm relatively new with ubuntu :smile: 

I found it easiest to start on the "dark side", setting up your win machine as a workgroup member (aka 'MSHOME'), assigning the box a host name, and setting up some folders or shares.

On the linux/ubuntu side, I found it as easy as in windows (only the names have changed) in that most things were automatic.

Once the system boots, linux should have id'd your nic and most likely your gateway, windows workgroup, and win host machine.  You need to go into System | Admin | Networking and select the General tab and make sure you have assigned a host name (you did this when you installed), and correct workgroup name for your network.

Oh yeh, you will be asked for your password to do this ;) 

That lets you see the windows box, but to share folders from ubuntu you need to use Synaptic (System | Admin | Synaptic ) and search for samba and install the server side of the netwroking software (not everyone wants to share their linux folders with a vulnerable windows box).

I forgot, you can actually do the above by just going into System | Admin Shared Folders and your should be prompted to install the server stuff if it isn;t already there.

Last but not least you have to use the terminal command line and enter the following:

sudo smbpasswd -a user

to add a user andpassword for accessing your linux box via samba (replace 'user' above with the actual username).  

that's it until you want the more esoteric!

Setting up an SMB printer is just as easy using System | Admin | Printing gui

good luck and I hope this helps

---

### Post by jetpeach on 2005-10-18
Thanks for the advice.  When I shared the folder the first time, it prompted me to install the Samba server side, so I've done that too.  I think the step I missed was enabling a samba password account.
Trying it now.

Yeah!  Thanks for the help, so I'm pretty satisfied since the only non-GUI step I had to do was "sudo smbpasswd -a username".

Thanks for the help,
jet

---

### Post by wjp.reg on 2005-10-18
> Yeah! Thanks for the help, so I'm pretty satisfied since the only non-GUI step I had to do was "sudo smbpasswd -a username".


Isn't ubuntu GREAT!!!! :KS 

Glad I could help..

---

