---
title: "Change Bootloader"
date: 2010-08-18
forum: Desktop Environments
---

### Post by polraudio on 2010-08-18
I tried looking all over but all i can find is people using Grub and not answering the question and i dont want to use Grub as the main one. Once the computer starts it going into Grub then i cacn chose between Ubuntu or Windows 7. I want it so i loads the Windows 7 boot loader first then i can chose Ubuntu or Windows 7. After i chose Ubuntu then it loads Grub.

**Example:**
[IMG]http://img835.imageshack.us/img835/2760/baa.png[/IMG]

I want to do it like it does it with Wubi but dont want to use Wubi.

Any ideas on how i can do this?

---

### Post by oldfred on 2010-08-18
If you want windows as your default you can use this:


Startup manager in synaptic will allow you to set boot default and the timeout even in lucid.

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu. You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.

You can even totally hide grub so it just boots into windows and only if you hit the shift key quickly do you get a menu.

I think what you are looking at is EasyBCD. It requires you to install grub2 to a partition which is unreliable (see messages on blocklists). So do not blame Ubuntu if you have problems.

---

### Post by Computer Guru on 2010-08-18
oldfred, EasyBCD no longer requires that you install GRUB2 to a partition. The new method is documented here: [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by oldfred on 2010-08-18
You may still have a problem if grub2 still thinks it is in the MBR. On the next update it will just reinstall itself.

We used this for portable users.

to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose drive, enter to accept, do not choose partitions

I copied this from another post:
Important for external removeable drives: Fixed 2010-02-04 for Lucid
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/496435](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/496435)
reinstalls grub and allows choice of which drive to install to. Choose boot drive if not sda
sudo dpkg-reconfigure grub-pc
I finally found out how to prevent the MBR to be overwritten.
I ran dpkg-reconfigure grub-pc and deselected /dev/sda which meant that the values field for grub-pc/install_devices in /var/cache/debconf/config.dat is now empty. Then nothing is written to the MBR or the boot sector when grub-pc gets updated. Occasionally I should probably rerun manually grub-install /dev/sda2 after grub-pc package updates to keep stage1 install in sync.

---

### Post by polraudio on 2010-08-19
> **Computer Guru said:**
> oldfred, EasyBCD no longer requires that you install GRUB2 to a partition. The new method is documented here: [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Thankyou very much. Followed them steps since im a EasyBCD user. Worked perfectly with no problems. 

Now i dont have to worrying about grub messing up like it always does sooner or later. Now when it does all i have to do is format the partition with linux on it and remove the Ubuntu option and reinstall ubuntu.

Thanks for making such a helpful tool.

EasyBCD Rocks!

---

### Post by mcduck on 2010-08-19
> **polraudio said:**
> 
Now i dont have to worrying about grub messing up like it always does sooner or later. Now when it does all i have to do is format the partition with linux on it and remove the Ubuntu option and reinstall ubuntu.

I've never even heard of Grub messing itself up, unless you have hand-edited it's configuration files and have done it in the wrong way (editing current options but not defining the default options, or moving third-party boot lines into the automagick kernel list section in old Grub, or editing the grub.cfg instead of the correct files in Grub2).

And even if that happened, why would you reinstal Ubuntu to fix that instead of just reinstalling Grub itself?

---

### Post by polraudio on 2010-08-19
> **mcduck said:**
> I've never even heard of Grub messing itself up, unless you have hand-edited it's configuration files and have done it in the wrong way (editing current options but not defining the default options, or moving third-party boot lines into the automagick kernel list section in old Grub, or editing the grub.cfg instead of the correct files in Grub2).

And even if that happened, why would you reinstal Ubuntu to fix that instead of just reinstalling Grub itself?
EDIT: didnt do any edits, dont even know anything about grub
because im new to the whole linux thing and when grub messes up and i cannot get on my computer im screwed because i have no access to the internet to get help till i install ubuntu again.

I hate entering commands because i always mess stuff up or cannot get the commands people tell me to work. I tried fixing the Rescue Grub thing by doing some things i found on the internet and couldn't get it to work so i reinstalled ubuntu.

Yea me and grub hate each-other lots. Well me and all command based things.

Is there a big list of commands and examples that i can just save so i can view them on my ipod or something incase it happens again?

---

