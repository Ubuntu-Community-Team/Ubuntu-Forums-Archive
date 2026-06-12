---
title: "Big trouble!!"
date: 2006-02-19
forum: Desktop Environments
---

### Post by KevNice on 2006-02-19
Well, I don't know how I did it. I tried downloading a newer version of FireFox, version 1.5.0.1. It came as a .tar.gz packaged file. I couldn't figure out how to install it (im still a Linux noob), so I checked the Mozilla site. They said to use the tar -xzvf command to unpack it. So I unpacked it but I didn't know what to do after that, nothing seemed to happen. I thought it was because I unpacked it to the wrong directory (i.e. the desktop, and not the mozilla directory). So I moved the tar.gz. file to /usr/lib/mozilla-firefox. I tried the regular tar -xzvf command, and it didn't seem to work (this shoulda been a warning). So I did it again using sudo, and it worked. But...

Now I can't seem to open mozilla. When I click on the icons, it says:

Details: Failed to execute child process 
"firefox" (Permission denied)

If I just type "firefox" in Terminal it says command not found.

The only reason I am able to post this is because I left a browser window open when I did the install, but I can't open any new ones. 

Please help! How do I fix it, and install the updated browser properly?

---

### Post by niviche on 2006-02-19
I can't help you as much as the new Firefox is concerned, but you might want to know that you have a second browser on your gnome desktop, called "Epiphany". It works very well, even though it doesn't have all the little things of Firefox, and it might help you to browse the net while your Firefox installation is broken.

---

### Post by rudiz on 2006-02-19
Try this

[https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29%7C%28version%29%7C%28new%29](https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29%7C%28version%29%7C%28new%29)

---

### Post by Lord Illidan on 2006-02-19
[quote=KevNice]Well, I don't know how I did it. I tried downloading a newer version of FireFox, version 1.5.0.1. It came as a .tar.gz packaged file. I couldn't figure out how to install it (im still a Linux noob), so I checked the Mozilla site. They said to use the tar -xzvf command to unpack it. So I unpacked it but I didn't know what to do after that, nothing seemed to happen. I thought it was because I unpacked it to the wrong directory (i.e. the desktop, and not the mozilla directory). So I moved the tar.gz. file to /usr/lib/mozilla-firefox. I tried the regular tar -xzvf command, and it didn't seem to work (this shoulda been a warning). So I did it again using sudo, and it worked. But...

Now I can't seem to open mozilla. When I click on the icons, it says:

Details: Failed to execute child process 
"firefox" (Permission denied)

If I just type "firefox" in Terminal it says command not found.

The only reason I am able to post this is because I left a browser window open when I did the install, but I can't open any new ones. 

Please help! How do I fix it, and install the updated browser properly?[/quote]

You unpacked it in the wrong folder. Take it away from there and put it in /opt/firefox

Then try running /opt/firefox/firefox from a terminal.

---

### Post by tmahmood on 2006-02-19
Please Check the permissions. as you have extracted all the files using sudo all permissions are set to root. so you have to set permission so that other users can read & execute.

PS:
what you have done might have broken Epiphany. thats mean your help browser is gone, you shouldn't have copied over the original mozilla-firefox.
well what done is done,if your help is not working reinstall the previous firefox from Synaptic.

---

### Post by saudoi on 2006-02-19
I also had this trouble at first time with Ubuntu. Luckily, i got the instruction as rudiz posted so that i could "upgrade" my firefox to the lastest version.

However, the Firefox 1.5.x still has problem with media player embedded into music online or movie online sites. Firefox will close All windows and tabs immediately :(

---

### Post by rudiz on 2006-02-19
To check for updates on FF 1.5 and later try this:

close FF

in terminal: sudo firefox

Help> Ceck for Updates

close FF en restartit again

thats it! ;-)

---

### Post by rudiz on 2006-02-19
@ saudoi

Did u removed totem-gstreamer allready?

Remove it ;-)

@KenNice

if u cant use FF at this moment use Epiphany... with sudo apt-get install epiphany-browser you install these second browser.

---

