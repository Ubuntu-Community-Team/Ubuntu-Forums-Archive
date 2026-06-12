---
title: "How to Install RtCW ???"
date: 2005-08-06
forum: Gaming &amp; Leisure
---

### Post by grofaz on 2005-08-06
I have the original game CD for the Windows version and I know how and where to get the Linux binaries but I don't know how to actually put it all together and make it work. Can anyone steer me towards an operational installation? Thanks!!

---

### Post by Mishura on 2005-08-07
_**Things You will need:**_

1.  Wolfenstein CD (This HOWTO uses the Non-GOTY version)
2.  Wine or Cedega (For extracting the files only, not for playing)

OK.  I assume you already have a working Wine installation.  If not, refer to another thread to learn how to install and set it up.

First, you will need two files:  the Linux RtCW 1.4 installer, and the Linux 1.41 patch installer.  The GoTY-Mappack installer is also a good idea.  Search either ftp.idsoftware.com or rtcwfiles.com as both include the files you will need.

Now, don't run the installers just yet.  You will need to extract the files from the CD.  However, they were compressed in such a way that it's nearly impossible to extract natively in Linux.  Stupid idea, but easily circumvented.

Mount your RtCW CD.  Run the setup executable through wine.  Extract *somewhere*..  just remember where you installed it.

After installation,  Run the Linux installers.  First the 1.4, then the patch.  GOTY-Mappack optional.

After that, you will need to copy the proper .pk3s files to your RtCW's base folder (rtcw/main/).  Copy all *.pk3 files from your wine install, to your linux native install.

After that... you should be ready to play.  I recommend removing or uninstalling your Wine Install of RtCW, as you will not need it.

Notes:

Don't use the 1.3* installers.  I've had game issues when using those.  MAKE SURE you start out with 1.4-full.  then 1.41-patch.  This is the PROVEN way (for me.)

And yes, you will need Wine.. or Windows.  I recommend backing up your packfiles (*.pk3) to a CD or something (Like I did) to prevent the need for Wine in the future.

And finally, the LIFLG (Loki Installers For LInux Games) installer for RtCW is broken, and you'll no longer find it on the webpage anyways.  I tried using this, and it was broken, and they haven't came up with a fix.  If you find an installer with a *-english.run deal at the end, don't bother using it.

---

### Post by grofaz on 2005-08-07
[QUOTE=Mishura]_**Things You will need:**_

1.  Wolfenstein CD (This HOWTO uses the Non-GOTY version)
2.  Wine or Cedega (For extracting the files only, not for playing)

OK.  I assume you already have a working Wine installation.  If not, refer to another thread to learn how to install and set it up.

First, you will need two files:  the Linux RtCW 1.4 installer, and the Linux 1.41 patch installer.  The GoTY-Mappack installer is also a good idea.  Search either ftp.idsoftware.com or rtcwfiles.com as both include the files you will need.

Now, don't run the installers just yet.  You will need to extract the files from the CD.  However, they were compressed in such a way that it's nearly impossible to extract natively in Linux.  Stupid idea, but easily circumvented.

Mount your RtCW CD.  Run the setup executable through wine.  Extract *somewhere*..  just remember where you installed it.

After installation,  Run the Linux installers.  First the 1.4, then the patch.  GOTY-Mappack optional.

After that, you will need to copy the proper .pk3s files to your RtCW's base folder (rtcw/main/).  Copy all *.pk3 files from your wine install, to your linux native install.

After that... you should be ready to play.  I recommend removing or uninstalling your Wine Install of RtCW, as you will not need it.

Notes:

Don't use the 1.3* installers.  I've had game issues when using those.  MAKE SURE you start out with 1.4-full.  then 1.41-patch.  This is the PROVEN way (for me.)

And yes, you will need Wine.. or Windows.  I recommend backing up your packfiles (*.pk3) to a CD or something (Like I did) to prevent the need for Wine in the future.

And finally, the LIFLG (Loki Installers For LInux Games) installer for RtCW is broken, and you'll no longer find it on the webpage anyways.  I tried using this, and it was broken, and they haven't came up with a fix.  If you find an installer with a *-english.run deal at the end, don't bother using it.[/QUOTE]

Is that all, just the *.pk3 files? It started up great but when I started loading an actual game I got an error message concerning a missing config file so I copied the WolfConfig.cfg file over as well. My question is are there any other files needed too?? This is really great, thanks for your help!

---

### Post by grofaz on 2005-08-07
Still getting the can't open/write to file error. Is it a permissions thing??

Yup, that's it. Use sudo wolfsp or wolfmp and you're good to go. Now if I could do the same for Far Cry...without using wine/cedega I'd be a happy camper.

Thanks for helping, I appreciate it.

Regards...

---

### Post by Mishura on 2005-08-07
> Still getting the can't open/write to file error. Is it a permissions thing??

Yup, that's it. Use sudo wolfsp or wolfmp and you're good to go. Now if I could do the same for Far Cry...without using wine/cedega I'd be a happy camper.

Thanks for helping, I appreciate it.

Regards...

Hmmm..  I can play it fine as non-root..  Where did you install it?  If you installed it outside of your home directory and still have permission problems, I suppose you can do a:

sudo chown $USERNAME:$USERNAME * -R

Substitute $USERNAME for your username.  Like:  "chown mishura:mishura * -R".  

In the root of your Wolfenstein directory (e.g.: /usr/local/games/wolf).  **Make sure you are in the correct directory when you do that.. **  I don't recommend playing games as root.  Bad juju.  (Then again, theoretically its not as insecure as playing a game in Windows.. but its just good policy.)

I'll admit that I am a bit rusty at installing Wolfenstein, since its been awhile that I had to do it the hard way (I have backed up .pk3 files).  And yes,  the pakfiles is all you need from your wolfenstein CD.  The Linux installers come with all the libraries and binaries needed.  It just needs the data.

---

### Post by grofaz on 2005-08-08
I reinstalled it on Windows first then made a rar archive. Transfered that to my ubuntu hard drive and copied the pk3 files into the wolf folder. So, if I simply change all the permissions to my user account I should be good to go then. I'll do that. Thanks again!

---

### Post by Mishura on 2005-08-09
Forgot to mention.. If you install it in your home directory (Such as ~/wolfenstein) you'll won't have to worry about permission problems anyways.  There are some games like Neverwinter Nights that require all the files to be owned by the user thats playing that game.  I used to install it all in /usr/local/games/nwn,  but lately i've been installing all my user apps in /home/mishura/apps/name_of_app (symlink the binaries to ~/bin or ~/.local/bin).

Its all preference anyways.  If you're the only user using that machine, then there really is no difference whether its installed as root or not.   You only worry about that if there is more than one user login on your machine, and you want all the users to play with it.

---

### Post by grofaz on 2005-08-09
I'm the only user on this machine and I installed it using the default path, which is "/usr/local/games/wolfenstein". I tried changing all the permissions to user but it still doesn't work right using "/home/user_name$ wolfsp". It can't open the wolfenstein.config file when you save a game which causes the error.. Works perfectly using sudo though.

I'll try reinstalling to my home directory and see if that solves the problem. I'd rather type less if I can. :)

---

### Post by mike998 on 2005-08-11
try 
```
chown -R user:user /usr/local/games/wolf
``` 
Basically, you want to make yourself owner of the wolf folder.  You may also want to use the command on the .wolf folder in your home directory.

---

### Post by grofaz on 2005-08-12
Hey Mike998, thanks! That did the trick. Much obliged.

Regards,
grofaz

---

### Post by fakie_flip on 2006-11-06
How is the online multiplayer part? I know the single player is really good, but i never tried multiplayer. I also know ET is good for that. I like all these games that run natively in Linux.

---

### Post by dmn_clown on 2006-11-08
> **Mishura said:**
> _**Things You will need:**_

1.  Wolfenstein CD (This HOWTO uses the Non-GOTY version)
2.  Wine or Cedega (For extracting the files only, not for playing)

OK.  I assume you already have a working Wine installation.  If not, refer to another thread to learn how to install and set it up.

First, you will need two files:  the Linux RtCW 1.4 installer, and the Linux 1.41 patch installer.  The GoTY-Mappack installer is also a good idea.  Search either ftp.idsoftware.com or rtcwfiles.com as both include the files you will need.

Now, don't run the installers just yet.  You will need to extract the files from the CD.  However, they were compressed in such a way that it's nearly impossible to extract natively in Linux.  Stupid idea, but easily circumvented.

Mount your RtCW CD.  Run the setup executable through wine.  Extract *somewhere*..  just remember where you installed it.

After installation,  Run the Linux installers.  First the 1.4, then the patch.  GOTY-Mappack optional.

After that, you will need to copy the proper .pk3s files to your RtCW's base folder (rtcw/main/).  Copy all *.pk3 files from your wine install, to your linux native install.

After that... you should be ready to play.  I recommend removing or uninstalling your Wine Install of RtCW, as you will not need it.

Notes:

Don't use the 1.3* installers.  I've had game issues when using those.  MAKE SURE you start out with 1.4-full.  then 1.41-patch.  This is the PROVEN way (for me.)

And yes, you will need Wine.. or Windows.  I recommend backing up your packfiles (*.pk3) to a CD or something (Like I did) to prevent the need for Wine in the future.

And finally, the LIFLG (Loki Installers For LInux Games) installer for RtCW is broken, and you'll no longer find it on the webpage anyways.  I tried using this, and it was broken, and they haven't came up with a fix.  If you find an installer with a *-english.run deal at the end, don't bother using it.

It would also be a good idea to use the updated binaries available from id's ftp server as they fix a security flaw in the game.

---

