---
title: "Usplash begins in graphic mode sequence but ends into command line mode"
date: 2009-01-01
forum: General Help
---

### Post by Terraman on 2009-01-01
Hi all,

I am customizing Ubuntu in a very old laptop (see signature). Firstly, I tried to install Splashy, but I could not make it work. So, I have installed Usplash, Usplash-Themes-Ubuntu, and Startupmanager. When the computer shuts down, the graphic boot sequence is correctly shown. However, when it starts, it begins showing a graphic sequence and at the end it shows the command line sequence.

How can I solve this problem?:confused:

Thanks in advance!

---

### Post by Tim Sharitt on 2009-01-02
When it switches to the terminal readout, are any errors displayed (such as something not loading)?

---

### Post by Terraman on 2009-01-02
Dear Tim,

As far as I can get, there are not errors displayed.

---

### Post by Terraman on 2009-01-06
Anyone?

---

### Post by Aearenda on 2009-01-06
It probably means that something is taking longer than is expected, but not failing - which is more likely on an old machine like yours. I notice this particularly on Intrepid on my older machine, but it doesn't always do it (it's not as old as yours). Usplash has timeouts that are set at various stages of startup, and if the next stage isn't reached before the timeout, it switches to the text display so you can see what is happening.

If you can spot what the last line of the text display is showing when it switches back, that might give us a clue as to how to fix it.

EDIT: I just remembered something from installing Debian a while ago - IIRC the /etc/rcS.d/S??console-setup procedure (where ?? is variable, and it links to /etc/init.d/console-setup) was doing something that triggered Usplash to switch back. The fix was to comment out a line, but I don't see the equivalent line in the Hardy version, so maybe this is a red herring.

---

### Post by caljohnsmith on 2009-01-06
Does the /etc/usplash.conf file have your correct monitor resolution? Also, please post the output of the following:
```
cat /etc/initramfs-tools/conf.d/resume
cat /etc/fstab
sudo blkid -c /dev/null
```

---

### Post by Terraman on 2009-01-09
caljohnsmith, these are the outputs:

cat /etc/initramfs-tools/conf.d/resume
cat: /etc/initramfs-tools/conf.d/resume: No such file or directory

cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>    <type>  <option>      <dump>   <pass>
proc            /proc            proc    defaluts      0        0
# /dev/hda5
UUID=1bd1dd50-835b-4cf6-b590-dbff4c83d446 / ext3 relatime,errors=remount-ro 0
# /dev/hda3
UUID=e553876-7f70-4e2d-a89a-9c3177ffa270  /home  ext3 relatime  0   2
# /dev/hda6
UUID=059716c6-818f-4ea3-bd3b-b4ca3b228d90 none swap sw 0        0
/dev/hdb        /media/cdrom0   ufd,iso9660 user,noauto,exec,utf8 0   0
/dev/fd0        /media/floppy0  auto      rw,user,noauto,exec,utf8 0   0

sudo blkid -c /dev/null
/dev/hda3: UUID="e5538e76-7f70-4e2d-a89a-9c3177ffa270" TYPE="ext3"
/dev/hda5: UUID="1bd1dd50-835b-4cf6-b590-dbff4c83d446"TYPE="ext3"
/dev/hda6: TYPE="swap" UUID="059761c6-818f-4ea3-bd3b-b4ca3b228d90"

---

### Post by caljohnsmith on 2009-01-09
It seems a little suspicious that you are missing the intramfs-tools resume file. Do you have initramfs-tools installed? How about posting the output of:
```
apt-cache policy initramfs-tools
```

---

### Post by Terraman on 2009-01-09
Aerenda,

The first text when it switches back to comman line is:

Reading files needed to boot....

The last text before running Slim:

Kinit: No resume image, doing normal boot...

I do not understand your EDIT's comment

---

### Post by Terraman on 2009-01-09
Sorry, caljohnsmith,

There was a typing error...

cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=059761c6-818f-4ea3-bd3b-b4ca3b228d90

---

### Post by forger on 2009-01-09
It's a bug: [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/203299](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/203299)

---

### Post by Aearenda on 2009-01-09
If it's that bug, there should be evidence. Terraman, can you post the output of ```
grep usplash /var/log/syslog
```It may be empty, but if usplash is crashing, we should find something there.

You can ignore my earlier incomprehensible edit, it's no longer relevant anyway. The usplash timeout at 'reading files needed to boot' is six minutes - so it shouldn't just be timing out.

Have you uninstalled splashy?

---

### Post by Terraman on 2009-01-09
> **Aearenda said:**
> If it's that bug, there should be evidence. Terraman, can you post the output of ```
grep usplash /var/log/syslog
```It may be empty, but if usplash is crashing, we should find something there.

You can ignore my earlier incomprehensible edit, it's no longer relevant anyway. The usplash timeout at 'reading files needed to boot' is six minutes - so it shouldn't just be timing out.

Have you uninstalled splashy?
Aearenda,

$ grep usplash /var/log/syslog
$

Thus, it is empty

Splashy is completly uninstalled

---

### Post by forger on 2009-01-10
try this:
```

grep usplash /var/log/kern.log
grep usplash /var/log/messages

```

---

### Post by Terraman on 2009-01-10
> **forger said:**
> try this:
```

grep usplash /var/log/kern.log
grep usplash /var/log/messages

```
forger,

$ grep usplash /var/log/kern.log
$
$ grep usplash /var/log/messages
$

---

### Post by Terraman on 2009-01-12
Nobody?

---

### Post by Aearenda on 2009-01-13
(We've had repeated forum outages.) I still think it's just that something is taking too long and usplash is timing out. Since it occurs with 'Reading files needed to boot' showing, you could try changing the behaviour so that it doesn't wait for that to finish. In the file /etc/init.d/readahead look for the bit that does the actual readahead and modify it by adding '--background' so it looks like this: ```
case "$1" in
    start|restart|force-reload)
        # This can take a while
        if type usplash_write >/dev/null 2>&1; then
            usplash_write "TIMEOUT 360" || true
        fi

        # If "profile" is placed on the kernel command-line we watch the boot
        # sequence and generate new readahead lists, rather than read the lists
        if ! grep -q "profile" /proc/cmdline; then
            log_begin_msg "Reading files needed to boot..."
# added --background in line below
            if /sbin/start-stop-daemon --start --quiet --background \
                --pidfile /var/run/readahead-list.bogus \
                --startas /sbin/readahead-list -- -s /etc/readahead/boot; then
                log_end_msg 0
            else
                log_end_msg $?
            fi
        else

```
Then see what happens - it should make the disk reading take place in the background, while the startup proceeds.

---

### Post by Terraman on 2009-01-14
> **Aearenda said:**
> (We've had repeated forum outages.) I still think it's just that something is taking too long and usplash is timing out. Since it occurs with 'Reading files needed to boot' showing, you could try changing the behaviour so that it doesn't wait for that to finish. In the file /etc/init.d/readahead look for the bit that does the actual readahead and modify it by adding '--background' so it looks like this: ```
case "$1" in
    start|restart|force-reload)
        # This can take a while
        if type usplash_write >/dev/null 2>&1; then
            usplash_write "TIMEOUT 360" || true
        fi

        # If "profile" is placed on the kernel command-line we watch the boot
        # sequence and generate new readahead lists, rather than read the lists
        if ! grep -q "profile" /proc/cmdline; then
            log_begin_msg "Reading files needed to boot..."
# added --background in line below
            if /sbin/start-stop-daemon --start --quiet --background \
                --pidfile /var/run/readahead-list.bogus \
                --startas /sbin/readahead-list -- -s /etc/readahead/boot; then
                log_end_msg 0
            else
                log_end_msg $?
            fi
        else

```
Then see what happens - it should make the disk reading take place in the background, while the startup proceeds.
Aearenda,

Unfortunately, it still shows the boot sequence.

---

### Post by Aearenda on 2009-01-14
Best to undo that change and stay standard, then - unless it makes your system start faster (it depends on the balance between cpu speed and disk throughput).

Maybe I have misunderstood what you said earlier:
> The first text when it switches back to comman line is:
Reading files needed to boot....
I have assumed this was the last line on the screen when it switches back to text mode - but are you really saying this is the first thing to appear *after* the switch?
If so, then the delay is happening earlier, in the last stages of the initramfs process. There are several folders for custom scripts there that are usually empty - let's make sure they are, and let's see what else is installed in the standard location under /usr/share. Please post the output from the following commands:
```
ls -R /etc/initramfs-tools
ls -R /usr/share/initramfs-tools
```

---

### Post by Terraman on 2009-01-15
Aerenda,

Yes, it is the first line to appear "after" the switch. I totally agree with you that it has to be in earlier stages.

> 
ls -R /etc/initramfs-tools
/etc/initramfs-tools:
conf.d  hooks   initramfs.conf   modules   scripts  update-initramfs.conf

/etc/initramfs-tools/conf.d
resume

/etc/initramfs-tools/hooks:

/etc/initramfs-tools/scripts:
init-bottom   init-top     local-premount   nfs-bottom    nfs-top
init-premount local-bottom local-top        nfs-premount

/etc/initramfs-tools/scripts/init-bottom:

/etc/initramfs-tools/scripts/init-premount:

/etc/initramfs-tools/scripts/init-top:

/etc/initramfs-tools/scripts/local-bottom:

/etc/initramfs-tools/scripts/local_premount:

/etc/initramfs-tools/scripts/local-top:

/etc/initramfs-tools/scripts/nfs-bottom:

/etc/initramfs-tools/scripts/nfs-premount:

/etc/initramfs-tools/scripts/nfs-top:

ls -R /usr/share/initramfs-tools
/usr/share/initramfs-tools:
conf-hooks.d   conf.d   hook-functions   hooks   init   modules   modules.d   scripts

/usr/share/initramfs-tools/conf-hooks-d:
cryptsetup

/usr/share/initramfs-tools/conf.d
uswusp

/usr/share/initramfs-tools/hooks:
console-setup  cryptopenct  cryptroot  fuse_utils   ntfs_3g udev    uswusp
console_tools  cryptonsc    dmsetup    kernelextras thermal usplash

/usr/share/initramfs-tools/modules.d:

/usr/share/initramfs-tools/scripts:
casper-premount  init-premount  local-bottom   nfs          nfs-top
functions        init-top       local-premount nfs-bottom
init-bottom      local          local-top      nfs-premount

/usr/share/initramfs-tools/scripts/casper-premount:

/usr/share/initramfs-tools/scripts/init-bottom:
udev

/usr/share/initramfs-tools/scripts/init-premount:
ps3  udev

/usr/share/initramfs-tools/scripts/init-top:
all_generic_ide  console_setup  frembuffer  usplash

/usr/share/initramfs-tools/scripts/local-bottom:
cryptopensc  ntfs_3g

/usr/share/initramfs-tools/scripts/local-premount:
ntfs_3g  resume  uswusp

/usr/share/initramfs-tools/scripts/local-top:
cryptopensc  cryptroot

/usr/share/initramfs-tools/scripts/nfs-bottom:

/usr/share/initramfs-tools/scripts/nfs-premount:

/usr/share/initramfs-tools/scripts/nfs-top:
udev



---

### Post by Aearenda on 2009-01-15
Hmm - the major difference between yours and one of my Hardy systems is all the crypto stuff - are you encrypting your root partition? That would slow things down...

BTW, did you type all that, rather than use copy/paste? 'frembuffer' would be 'framebuffer' really.

---

### Post by johnjohn2 on 2009-01-16
What i suggest as i had the same issues on an AMD 6400 Ati 4870 8 g ram desktop is to disable fsck.

Read about all the cons first as if anything goes wrong with your disk you will have to run the command.

Check this out

[http://www.linuxforums.org/forum/ubuntu-help/88818-disabling-fsck-startup.html](http://www.linuxforums.org/forum/ubuntu-help/88818-disabling-fsck-startup.html)

Hope it helps

John

:guitar:

---

### Post by Terraman on 2009-01-16
> **Aearenda said:**
> Hmm - the major difference between yours and one of my Hardy systems is all the crypto stuff - are you encrypting your root partition? That would slow things down...

BTW, did you type all that, rather than use copy/paste? 'frembuffer' would be 'framebuffer' really.
Aearenda,

Yes, I have copied all these, I do not know why, but copy and past does not work.

How do I know if my root partition is being encrypted? And, if so, how can I diseable it?

---

### Post by johnjohn2 on 2009-01-16
Have you tried disabling FSCK Without doing that none of the other suggestions may help


:popcorn:

---

### Post by Terraman on 2009-01-16
> **johnjohn2 said:**
> What i suggest as i had the same issues on an AMD 6400 Ati 4870 8 g ram desktop is to disable fsck.

Read about all the cons first as if anything goes wrong with your disk you will have to run the command.

Check this out

[http://www.linuxforums.org/forum/ubuntu-help/88818-disabling-fsck-startup.html](http://www.linuxforums.org/forum/ubuntu-help/88818-disabling-fsck-startup.html)

Hope it helps

John

:guitar:
johnjohn2,

The command fsck does not check every boot, as far as I know, it cheks every 29 boots or so. Furthermore, this command comes after the "switch".

---

### Post by johnjohn2 on 2009-01-16
> **Terraman said:**
> johnjohn2,

The command fsck does not check every boot, as far as I know, it cheks every 29 boots or so. Furthermore, this command comes after the "switch".

Look it did with mine that is all i am saying.

---

### Post by Terraman on 2009-01-16
> **johnjohn2 said:**
> Look it did with mine that is all i am saying.
johnjohn2,

Thank you very much! Do not misunderstand my reply. I was generally informing in a quick replay! Maybe it was not very polite. Sorry, if you have felt that way, it was not my intention at all.

---

### Post by johnjohn2 on 2009-01-16
> **Terraman said:**
> johnjohn2,

Thank you very much! Do not misunderstand my reply. I was generally informing in a quick replay! Maybe it was not very polite. Sorry, if you have felt that way, it was not my intention at all.

Look man dont worry.

Thanks for the apology but truly none needed

The thing with fsck is that you may think that it only runs every 29 days but not if you have a home directory on the same partition.

Peace be with you

John :D

---

### Post by Terraman on 2009-01-16
> **johnjohn2 said:**
> Look man dont worry.

Thanks for the apology but truly none needed

The thing with fsck is that you may think that it only runs every 29 days but not if you have a home directory on the same partition.

Peace be with you

John :D
johnjohn2

Yes, your right indeed, in this laptop, my home directory is not in the same partition. Nevertheless, when fsck runs, it checks both partitions.

---

### Post by johnjohn2 on 2009-01-16
> **Terraman said:**
> johnjohn2

Yes, your right indeed, in this laptop, my home directory is not in the same partition. Nevertheless, when fsck runs, it checks both partitions.

Check the file by doing > gksu gedit /etc/fstab in terminal

if any partitions have a 1 next to them as shown in the link i sent you it means fsck is checking the partition every time!

Regards John

:guitar:

---

### Post by Aearenda on 2009-01-16
Ummm....that thread is a bit misleading.... Putting a 0 on the end of the line in /etc/fstab will indeed suppress the fsck, but having a 1 there doesn't mean 'always do it', it just means 'do this one first'. The root partition normally has a 1 there, and the others have 2, which means 'do these second'. Do 'man fstab' in a terminal to see the spec.

The fsck check runs according to a setting on the partition itself. **That setting** is checked on every boot; the actual check typically runs much less often than that. For ext2 and ext3 partitions you use 'tune2fs' to set the interval, and it can set to count so many boots, or an interval of so many days, or disabled completely. See 'man tune2fs' for more. In a nutshell, try this if you want to set it to run every 4 weeks on partition /dev/sda1:
```
sudo tune2fs -i 4w /dev/sda1
```
And this will set the count to zero, which means the number of reboots won't affect things:
```
sudo tune2fs -c 0 /dev/sda1
```
I don't recommend turning the check off entirely. It can pick up possible problems before they become serious.
This will tell you what (all) the settings are now:
```
sudo tune2fs -l /dev/sda1
```
Or, to get less extra stuff, ```
sudo tune2fs -l /dev/sda1 | grep [Mm]ount
sudo tune2fs -l /dev/sda1 | grep [Cc]heck
```


Terraman, to copy from a terminal window, you select with the mouse then use CTRL+SHIFT+C, or the edit menu. It does work - you shouldn't have had to type all that! But it won't work if you switch away from the GUI into a full-screen terminal using CTRL+ALT+F1. If you are doing this, you can redirect the output into a file by adding >myfilename to the end of the command (e.g 'ls -R /usr/share/initramfs-tools >myfilename'), and then pick that up in the GUI session using 'gedit myfilename' making sure that you include the folder name as well if you have changed away from your home folder in the terminal. If you want to see the output as well as save it, use 'tee' like this: 'ls -R /usr/share/initramfs-tools | tee myfilename'

Your root partition won't be encrypted if you didn't choose to make it so. We are no closer to solving your problem. If I get time this weekend I will see if I can set up Hardy on a similar old system and see what happens. It would be helpful to know how you did your original installation - was it from the Alternate CD? Did you build a command line system and then add stuff?

---

### Post by Terraman on 2009-01-16
Aearenda,

Yes, I have installed Hardy from an Alternate CD starting from a command line. I use Openbox as WM, Slim as login manager, and X.

I really do not remember where the root partition's encryption could have been chosen. Anyway, you have to bear in mind that despite the fact that you are installing a command line system, it will take a lot of time in an elderly computer. In my case it has taken 24 hours.

I have completely forgotten to add the SHIFT.

Thank you very much for your instructions.

---

### Post by Terraman on 2009-01-17
Aearenda,

I have turned off readahead and as far as I can get, the disks' encryption.

Thus, the first line that appears after the "switch" is:> preparing restricted drivers...

---

### Post by Aearenda on 2009-01-17
My 'tardy Hardy' system is installing the kernel at the moment - it's a 64Mb 233MHz Pentium-MMX desktop. Then I'll have to bring it up to date, and install usplash, slim and X. I'll use LXDE, it shouldn't affect the startup process, and I want to see how well it performs on this hardware. It runs really well on an old Transmeta-based laptop I have.

---

### Post by Aearenda on 2009-01-18
Mine flipped back to text mode on 'loading restricted drivers' too. I don't have readahead installed, or any encryption. On such low-memory systems, removing readahead is probably the key to your original problem - there's no free memory to cache things in. Silly of me not to realise that before.

Since my system needs no restricted drivers, I just removed that link from /etc/rcS.d, and it now stays in usplash almost to the end of startup. I have found before that the fix for that is to start slim before usplash stops - by ```
sudo mv /etc/rc2.d/S99slim /etc/rc2.d/S70slim
```

So, does your system need any restricted drivers? That means the lt modem drivers, atheros wireless, nvidia or ati video drivers. You can edit /etc/default/linux-restricted-modules-common to add unused ones to the disabled list, which should speed things up. I put the link back in /etc/rcS.d and added everything to the disabled list, as shown in the comment in that file, and usplash stayed put.

Next, I found it flipped on shutdown, for a while. I have come across that with slim before too - it doesn't tell usplash to come up at shutdown. What works for me is to modify /etc/init.d/usplash so that it calls usplash_down immediately before the call to usplash_write when told to stop, like this (only showing the relevant part):```
stop)
	if grep -q splash /proc/cmdline; then
		# -------- Next two lines are added -------------
		usplash_down
		sleep 1s
		usplash_write "TIMEOUT 15"
	fi
	;;

```

Try these suggestions and see how you get on :-)

---

### Post by Terraman on 2009-01-18
> **Aearenda said:**
> Mine flipped back to text mode on 'loading restricted drivers' too. I don't have readahead installed, or any encryption. On such low-memory systems, removing readahead is probably the key to your original problem - there's no free memory to cache things in. Silly of me not to realise that before.

Since my system needs no restricted drivers, I just removed that link from /etc/rcS.d, and it now stays in usplash almost to the end of startup. I have found before that the fix for that is to start slim before usplash stops - by ```
sudo mv /etc/rc2.d/S99slim /etc/rc2.d/S70slim
```

So, does your system need any restricted drivers? That means the lt modem drivers, atheros wireless, nvidia or ati video drivers. You can edit /etc/default/linux-restricted-modules-common to add unused ones to the disabled list, which should speed things up. I put the link back in /etc/rcS.d and added everything to the disabled list, as shown in the comment in that file, and usplash stayed put.

Next, I found it flipped on shutdown, for a while. I have come across that with slim before too - it doesn't tell usplash to come up at shutdown. What works for me is to modify /etc/init.d/usplash so that it calls usplash_down immediately before the call to usplash_write when told to stop, like this (only showing the relevant part):```
stop)
	if grep -q splash /proc/cmdline; then
		# -------- Next two lines are added -------------
		usplash_down
		sleep 1s
		usplash_write "TIMEOUT 15"
	fi
	;;

```

Try these suggestions and see how you get on :-)
Thank you very much, Aearenda!

I have followed your instructions and it works well now.

PS: Does LXDE perform better then X in this old machine?

---

### Post by Aearenda on 2009-01-18
That's great! Well done.

LXDE stands for 'lightweight X11 desktop environment' - it uses X for the display subsystem, and OpenBox for the window manager. I like it because it is less 'exotic' than some other lightweight systems, and so easier to teach others how to use when Windows is all they have used before. It is way faster than Xubuntu, noticeably faster than plain XFCE, and probably about the same as IceWM and native OpenBox/FluxBox etc. [http://lxde.org/](http://lxde.org/)

---

### Post by Terraman on 2009-01-20
> **Aearenda said:**
> That's great! Well done.

LXDE stands for 'lightweight X11 desktop environment' - it uses X for the display subsystem, and OpenBox for the window manager. I like it because it is less 'exotic' than some other lightweight systems, and so easier to teach others how to use when Windows is all they have used before. It is way faster than Xubuntu, noticeably faster than plain XFCE, and probably about the same as IceWM and native OpenBox/FluxBox etc. [http://lxde.org/](http://lxde.org/)
I've tried it and I like it very much.

Thank you very much again!

---

