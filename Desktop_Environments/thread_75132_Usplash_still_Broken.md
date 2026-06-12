---
title: "Usplash still Broken"
date: 2005-10-13
forum: Desktop Environments
---

### Post by gbusse on 2005-10-13
Sorry if this is in the wrong place but I am not quite sure where to put it. After a clean installation of the released Breezy, Usplash is still not working properly. Here is what happens:

- Usplash appears
- The message "Loading modules" is displayed at the bottom of the screen
- After about 5 seconds Usplash dissapears and the old text based boot messages are displayed

I submitted bug reports about this problem after the release of Colony 5 and the RC. I guess I will go and add some more notes to those bug reports regarding the problem still existing with the release.

Is anyone else having this problem or am I the only one?!?

Thanks,
Gord

---

### Post by Triton on 2005-10-13
No, I'm not having any problems.  I did read in the old developer forum for breezy that a command line apt-get would update or repair it.  Unfortuately I can't remember what that was.

:(

---

### Post by serzz on 2005-10-13
It goes back to text mode if it gets any errors, I think. So all you need to do is fix them.

---

### Post by gbusse on 2005-10-13
[QUOTE=serzz]It goes back to text mode if it gets any errors, I think. So all you need to do is fix them.[/QUOTE]

How can I find out what the errors are? There are no error messages printed on the boot screen?

Thanks,
Gord

---

### Post by Emerzen on 2005-10-13
Often if you switch to the first terminal (ctrl+alt+f1) error messages from boot will be sitting there.  To get back to GUI -> ctrl+alt+f7

---

### Post by serzz on 2005-10-13
Hmm, then I think it would be hard to find any if you don't have them. I've been using Breezy from PR version, never had anything like this.

---

### Post by gbusse on 2005-10-13
Thanks for your suggestions. I will do some digging around in my system and logs to see if I can figure anything out and will report back my findings in case there is anyone else having the problem.

Since Usplash seems to be aborting during the "Loading modules" phase would it be a good assumption that there is a piece of hardware that is not loading properly? Would that be a good place to start looking?

Thanks again,
Gord

P.S. Other than this Usplash problem (which I admit is minor) I have not had any other problems that I could not work around in Breezy and am otherwise very happy with it....

Thank to the Devs for the great work....

---

### Post by ezHiker on 2005-10-13
I don't have a resolution for your, but if it makes you feel any better, the same thing is happening to me too on my Thinkpad T42 with ATI video.  

It doesn't affect my desktop which has an nvidia card. 

It hasn't irritated me enough yet to attempt to fix it, though.

---

### Post by linuxlizard on 2005-10-13
I had the same problem. I think I fixed it by installing kubuntu-artwork-bootsplash and then usplash again. I sort of think I might have done something else with grub but don't remember for sure, and can't find anything in my grub file that would have made a difference, so maybe installing kubuntus splash (I did it accidently and didn't know it was kubuntus until I rebooted and saw it) and then afterwards reinstalling usplash will fix the prob. Sort of a ragged way to fix the problem, but mine works fine now.

---

### Post by ssam on 2005-10-13
it will also drop to text mode if somthing takes too long. maybe there is a default timeout setting that can be increased.

---

### Post by David Muench on 2005-10-13
I'd put my money on the timeout. My thinkpad T42 works fine with usplash. But my Progear webpad (old, Transmeta 400mhz cpu) which boots _really_ slowly shows the same behavior as the original poster. usplash exits and there are no apparent errors to cause it to.

---

### Post by gbusse on 2005-10-13
[QUOTE=David Muench]I'd put my money on the timeout. My thinkpad T42 works fine with usplash. But my Progear webpad (old, Transmeta 400mhz cpu) which boots _really_ slowly shows the same behavior as the original poster. usplash exits and there are no apparent errors to cause it to.[/QUOTE]

Thanks again people for all of the ideas. I like the timeout idea, now I just have to figure out where the adjust that. I just got home from work and will be looking at this tonight. If I find anything out I will post my results.

Although it would be kind of wierd it it was a timeout issue as this PC is a 2.4GHz P4 with 1GB of Ram and a 7200RPM 120GB HDD.

Later,
Gord

---

### Post by Emerzen on 2005-10-13
Just to mention, I've had this error but only after updating my kernel-images...I would get an "insmod" error. 

To fix that error:

**sudo dpkg-reconfigure linux-image-`uname -r`**

Also, if a module is taking too long to load it will revert to text...occassionally I get that when trying to connect to the ubuntu time servers...you can disable this service during boot and retry.

---

### Post by cjtopher on 2005-10-14
sudo usplash_write "TIMEOUT 120"

---

### Post by linuxlizard on 2005-10-14
try installing bum with synaptic. You can turn usplash off and on in bum- probably will find you must need to check the box to turn it on.

---

### Post by sabaoth on 2005-10-28
[QUOTE=cjtopher]sudo usplash_write "TIMEOUT 120"[/QUOTE]

Yeah, the same problem here with a Toshiba centrino 1.4. It freezes at startup (when loading the modules) for some seconds. The total process takes 31 seconds, and afterwards usplash has gone.

With this script:

```

usplash &
usplash_write "TIMEOUT 30"
sleep 1
usplash_write "TEXT hello"
sleep 0.5
usplash_write "FAILURE no"
sleep 1
usplash_write "TEXT test"
sleep 0.5
usplash_write "SUCCESS yes"
sleep 20
usplash_write "PROGRESS 20"
sleep 1
usplash_write "PROGRESS 40"
sleep 1
usplash_write "QUIT"


```

I realized that the default timeout is 15 seconds. To solve this I should put that usplash_write "TIMEOUT 60" that was suggested before somewhere - I guess the rcN.d script would be a good place, but haven't tried yet.

¿Some idea at this point?

By the way, someone said before that reconfiguring the linux-image package would work. Well, it works if the problem is the video mode as reconfiguring linux-image remakes /boot/grub/menu.lst (usplash seems to work only with the default video mode... not with vga=971 or vga 972).

Cheers,

Fran.

---

### Post by sabaoth on 2005-10-29
It was the timeout indeed. The place to modify the timeout is the very moment in which you load usplash - to override problems even in the first stages of init.

The file which loads usplash should be in /usr/share/initramfs-tools/scripts/init-top/ (Breezy), but try a "locate usplash" and you should get something like this:

```
...
/usr/share/doc/usplash/changelog.Debian.gz
/usr/share/initramfs-tools/hooks/usplash
/usr/share/initramfs-tools/scripts/init-top/usplash
/sbin/usplash_write
/sbin/usplash
```

So edit the file with "sudo nano /usr/share/initramfs-tools/scripts/init-top/usplash", and go to the end of the file. There you'll find this line:

```
/sbin/usplash -c &
```

And we write there:

```
echo Launching usplash...
sleep 1
/sbin/usplash -c &
sleep 1
/sbin/usplash_write "TIMEOUT 60"
```

So we send he TIMEOUT order just after loading usplash. The first echo and sleep is just to have visual confirmation we indeed modified this.

IMPORTANT: One last thing is make a "sudo dpkg-reconfigure linux-image-$(uname -r)", so the initrd image is rebuilt and our changes are applied.

If everything went right, when restarting, you should see:

Lanunching usplash...

and, after one second, the usplash will be loaded with the new TIMEOUT. Services like dhcpd sometimes have a long timeout if they're not successfull, so change the usplash timeout to fit your needs.

Anyways, would be nice if the usplash guys would configure a larger timeout by default, as it seems lots of people are having problems with that 15 seconds...

Fran.

---

