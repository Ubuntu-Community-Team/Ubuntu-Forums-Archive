---
title: "KDE Desktop broken, completely frozen"
date: 2011-02-09
forum: Desktop Environments
---

### Post by dave.kts on 2011-02-09
I have KXstudio 64 installed, was changing the clock font and doing little, normal tweaks to the panel, pulled the edge in a little, and it just froze right there, and now the whole desktop is broken, unresponsive. Nothing works. I have yaquake terminal installed so i can access a terminal by hitting F12, and open applications that way, but no menu's, links, widgets, panel icons or anything are working at all, after rebooting, logging in as other user, nothing helps.  I tried a apt-get install kdm or something like that, it didnt help tho.

If the easiest thing to do is ditch the stupid buggy KDE desktop and switch to GNOME- then i'd prefer that. If someone could help me sort this out it would be great. 

even while using the terminal, or applications opened thru it, it freezes periodically and i sit for a few minutes and it comes back. still no desktop tho.  Also the login was bugging out, i could click on a text field but the keys werent being recorded. couldnt type. cancelled, and next try i could type.

---

### Post by inobe on 2011-02-09
delete the hidden .kde folder, it'll reset your desk to out of the box settings.

you claim the desk is buggy, i assure past versions before kde 4.5 were very buggy, however kde 4.6 is out!

us kde fans stay on top of the game and upgrade to the latest and greatest, i suggest you have a look at that, but as with any desktop, individual results will vary ;)

---

### Post by dave.kts on 2011-02-10
well now im just stuck with no graphical interface, just command line login. tried reinstalling kdm.  and was telling me kde4 couldnt be found.
Where is the location of that folder?

---

### Post by dave.kts on 2011-02-14
well I tell you what Im not a KDE fan after this, id like to know if I can switch to gnome.
Help?

can't find a hidden folder with just ".kde"

---

### Post by inobe on 2011-02-14
here are the supported ubuntu derivatives.

[http://www.ubuntu.com/project/derivatives](http://www.ubuntu.com/project/derivatives)

kxstudio may have an ubuntu base, but i never seen or heard of it today.

here is their website [http://kxstudio.sourceforge.net/](http://kxstudio.sourceforge.net/)

i don't know if they have a forum, they should, it's their distribution!


but if you are interested in an actual ubuntu derivative, have a look at ubuntu studio, it uses the gnome desktop.

---

### Post by dave.kts on 2011-02-16
No, there is no support forum, he just directs you here, pretty much claiming that "an ubuntu problem will be a Kxstudio problem"... I was hoping he would find my thread and help me out with this but i guess its high hopes.
I have tried like 15 different distro's, including Ubuntu studio, and the KXstudio has the features I want (64 bit, native VSTi support, Jack pre-configured and working smooth in realtime for me out of the box, (Jack only has worked correctly for me out of the box on say, only 2 of the distro's ive tried).
I guess my point is that KXstudio seems to be put together pretty well and had the most appeal to me... But the KDE has just completely unimpressed me, whether it's my hardware at fault, KDE in general, or the compilation of it in this distro.
Its just not there at all now. 
So should i just forget about it, install a different distro?
I hate throwing in the towel, i've installed and reinstalled soooo many distros and things just keep going 100% wrong with just about anything. (even now in ubuntu 10.10 I have an update manager that fails all my updates. Something is always broken.

---

### Post by ankspo71 on 2011-02-16
Hi,
The .kde folder is located right inside your home folder. 
a command to remove it would be:
```
rm -rf ~/.kde
```
If you think there is anything in there you might need to keep, it would be better to rename it:
```
mv ~/.kde ~/.kdebackup
```

(I've seen some distributions use .kde4 as the default KDE configuration folder, so if .kde isn't present, delete or rename the .kde4 folder)

Now you can reboot with the command:
```
sudo reboot
```

Your KDE desktop should be restored now.

Next, comes repairing your update manager and install the latest updates in Ubuntu 10.10 (and more than likely KXstudio too) with commands.

Try using these commands one at a time:
```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade
```

Hope this helps.

---

### Post by ankspo71 on 2011-02-16
It is possible to remove KDE and replace it with Gnome.

Here is a link to completely remove kubuntu-desktop (kde4) and all Kubuntu's default applications, and then replace it with ubuntu-desktop (gnome) with all of Ubuntu's default applications, using a single command. These instructions are for *ubuntu 10.04 which is what KXstudio is based upon. 
[http://www.psychocats.net/ubuntu/puregnomelucid](http://www.psychocats.net/ubuntu/puregnomelucid) 

Hope this helps.

---

### Post by dave.kts on 2011-02-17
Thank you ankspo71
ran the first line in terminal that you suggested, trying to fix updates in ubuntu 10.10 and this is my output:

Setting up linux-image-2.6.35-22-generic (2.6.35-22.35) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-22.33 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-22.33 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
 * dkms: running auto installation service for kernel 2.6.35-22-generic                                                                                                                                         
 *       fglrx (8.780)...                                                                                                                                                                                [ OK ] 
 *       nvidia-current (260.19.06)...                                                                                                                                                                   [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
/etc/default/grub: 11: xforcevesa: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.35-25-generic (2.6.35-25.44) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-25-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
 * dkms: running auto installation service for kernel 2.6.35-25-generic                                                                                                                                         
 *       fglrx (8.780)...                                                                                                                                                                                [ OK ] 
 *       nvidia-current (260.19.06)...                                                                                                                                                                   [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
/etc/default/grub: 11: xforcevesa: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-25-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-25-generic; however:
  Package linux-image-2.6.35-25-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.25.32); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.35-22-generic
 linux-image-2.6.35-25-generic
 linux-image-generic
 linux-generic
david@ubuntu:~$ 

Looks rather serious, I don't know what to think about the Nvidia drivers, if that has anything to do with it. I havent installed much else since I've installed this system, only OpenArena, a couple other applications and thats it. 
Every once in a while my screens black out for a second or two, sometimes after losing mouse response for up to 5 seconds. Seems to me the Nvidia drivers have never been 100%, I dont know if that is the cause.

Thanks again for the help with KDE, ill get to work on it and see what happens

---

