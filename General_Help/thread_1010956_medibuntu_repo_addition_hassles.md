---
title: "medibuntu repo addition hassles"
date: 2008-12-14
forum: General Help
---

### Post by Nux Muncher on 2008-12-14
Hi, I just added medibuntu repos to add google-earth, among other programs, thru synaptic.  But when I start synaptic, I get the following error:

**W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A27**83

whatup wit dat?

s

---

### Post by Arup on 2008-12-14
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

paste this in your terminal.

---

### Post by Nux Muncher on 2008-12-14
Thanks Arup!!  I would post a 'thanks' but don't know how to do that =(... still new at this.

Cheers brother =)

---

### Post by Nux Muncher on 2008-12-14
... wait.. how come I don't see google earth in synaptic?

thanks in advance

s

---

### Post by drs305 on 2008-12-14
> **Nux Muncher said:**
> ... wait.. how come I don't see google earth in synaptic?



Can you run GoogleEarth? Applications, Internet, Google Earth.

You can see the status of installed/uninstalled packages by running this. Check the "State:" line. Change the version to 4.2 if 4.3 is not found:
```

aptitude show googleearth-4.3
*or for less output:*
aptitude show googleearth-4.3 | grep "State"

```

In answer to your question, you give thanks by clicking the small 'medal' red/gold icon in the lower right corner of the specific post.

---

### Post by Therion on 2008-12-14
To install Google Earth  you'll need to download the Linux installer from here (save it to your desktop):

[http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

Open a terminal and change to the directory where the installer downloaded to:```
cd ~/Desktop
```

Now you need to change the permissions on the installer so you can run it:```
chmod +x GoogleEarthLinux.bin
```

Lastly, run the installer as the root user:```
sudo ./GoogleEarthLinux.bin
```

Follow the prompts and you're all set.

---

### Post by Nux Muncher on 2008-12-14
Hi,

State for google earth is 'not installed'.

---

### Post by Nux Muncher on 2008-12-14
Hi, I want to be careful here because I reinstalled ibex due to G-E wonkiness.  Please advise most stable version (4.2 or 4.3) and give detailed installation instructions because (prior to ibex re-install) I'd installed G-E from G-E website.  If I follow your instructions above from terminal desktop prompt, i.e. "me@me-compnameDesktop:~$" ... will that work out?  and should I follow all defaults for installation process?  I know that home vs. opt directiories caused me confusion on my last try.

I know you're experienced user, but if you're going to explain anything beyond straight instructions,  please qualify that help and use simple terms if possible.

Thanks in advance

s

Thanks

---

### Post by Therion on 2008-12-14
> **Nux Muncher said:**
> Hi, I want to be careful here because I reinstalled ibex due to G-E wonkiness.  Please advise most stable version (4.2 or 4.3) and give detailed installation instructions because (prior to ibex re-install) I'd installed G-E from G-E website.  If I follow your instructions above from terminal desktop prompt, i.e. "me@me-compnameDesktop:~$" ... will that work out?  and should I follow all defaults for installation process?  I know that home vs. opt directiories caused me confusion on my last try.

I know you're experienced user, but if you're going to explain anything beyond straight instructions,  please qualify that help and use simple terms if possible.
Well... Uh, I thought I was qualifying the help and using simple terms.  You need to open a Terminal and cut and paste the commands into it.  The explanation for each command is given prior to the command itself.  

I can't promise you your GE install won't be "wonky" because GE is known to have issues with things like Compiz and certain file permissions. 

If my explanation isn't simple enough for you to understand fully it might be better if you wait for someone else who can offer you a different or simpler explanation that you can understand fully.

In truth, the post above is about as simple as I know how to make it.

Good luck!

---

### Post by Nux Muncher on 2008-12-14
> **Therion said:**
> Well... Uh, I thought I was qualifying the help and using simple terms.  You need to open a Terminal and cut and paste the commands into it.  The explanation for each command is given prior to the command itself.  

I can't promise you your GE install won't be "wonky" because GE is known to have issues with things like Compiz and certain file permissions. 

If my explanation isn't simple enough for you to understand fully it might be better if you wait for someone else who can offer you a different or simpler explanation that you can understand fully.

In truth, the post above is about as simple as I know how to make it.

Good luck!

Hi, I get following error at chmod command:
[B]
stav@stav-UBUdesktop:~$ cd ~desktop
bash: cd: ~desktop: No such file or directory
stav@stav-UBUdesktop:~$ dir
Desktop  Documents  Examples  Music  Pictures  Public  Templates  Videos
stav@stav-UBUdesktop:~$ chmod +x GoogleEarthLinux.bin
chmod: cannot access `GoogleEarthLinux.bin': No such file or directory
stav@stav-UBUdesktop:~$ sudo chmod +x GoogleEarthLinux.bin
[sudo] password for stav: 
chmod: cannot access `GoogleEarthLinux.bin': No such file or directory[/B]

I'm sorry if my last message made me sound lost... I'm just trying to learn this OS.  

s

---

### Post by oldos2er on 2008-12-14
You should copy and paste the commands Therion gave you. Linux is case-sensitive, so "cd desktop" is not the same as "cd Desktop".

---

### Post by Nux Muncher on 2008-12-14
Thanks Ann,  Do you know if Intrepid has compiz by default? .. and if Therion is right about potential problems, then I'd like to remove it as I'm testing this computer for work.  I don't need any bells and whistles to complicate matters at this point.

Correct me if I'm wrong, but 'compiz' is the GUI eye-candy that is set out of /system appearance/visual effects?  I've set mine to 'normal' ...will that diminish performance of any of my programs?

Genuine Thanx 4 your help =)

---

### Post by oldos2er on 2008-12-14
"Do you know if Intrepid has compiz by default?"

 Yes, I know; and yes, it does. To disable compiz, go to System, Preferences, Appearance, Visual Effects, and check 'None'. Whether or not running compiz affects performance depends on your hardware. If you have a newer, high-end video card it shouldn't slow things down.

---

### Post by Nux Muncher on 2008-12-14
Hi Ann,..G-E crapped-out again...just staring at stars.  After which I set visual effects to 'none'.  Should I bother trying to re-install G-E 4.2?  Is this a graphics problem?  AAAAUUUUGGGGHHHH! Why can't I uninstall G-E from Synaptic.  I'm vexed.

---

### Post by frankleeee on 2008-12-14
You can install from the medibuntu site if your running Intrepid here is a link.
[http://packages.medibuntu.org/intrepid/index.html](http://packages.medibuntu.org/intrepid/index.html)
And here is the site, if your running another distro.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by oldos2er on 2008-12-15
> **Nux Muncher said:**
> Hi Ann,..G-E crapped-out again...just staring at stars.  After which I set visual effects to 'none'.  Should I bother trying to re-install G-E 4.2?  Is this a graphics problem?  AAAAUUUUGGGGHHHH! Why can't I uninstall G-E from Synaptic.  I'm vexed.

 Since you installed GE "manually", i.e., without using one of Ubuntu's package managers, Synaptic doesn't know it's there and can't uninstall it. There should be an uninstall script in /opt/google-earth/uninstall, you'll probably need to run as root.

 I've heard of the error you describe, seeing only a star field with no earth, but I don't know if it's a video card/driver error or what. All I can tell you is I have an Nvidia GeForce 7300 LE running the 177.82 driver, with compiz-fusion enabled, and GE v4.3.7284.3916 beta, and it all works fine. I've never used the GE version available in the repositories; but maybe trying it will work for you.

---

