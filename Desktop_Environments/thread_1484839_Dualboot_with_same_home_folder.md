---
title: "Dualboot with same /home folder"
date: 2010-05-16
forum: Desktop Environments
---

### Post by sunk8 on 2010-05-16
Well, I'm trying something really wicked here...
I love distro-hopping and so have come up with a novel plan...
My parents use Windoze on the primary partition; so I'm dual-booting here. All other partitions are logical drives i.e. parts of an extended partition...
I've installed Ubuntu 10.04 on my PC with /boot and /home on different partitions. This is supposed to be my basic OS...
Now I have about 30 GB free on my extended; so I'm planning to install another distro here (Don't ask me why)... I wanna try Fedora; Mandriva; PCLinuxOS; OpenSUSE; LinuxMint; Gentoo and many more...

So, my question is: Can I use users on my /home partition directly into the other distro? i.e. I don't want to make another user there. And wanna have all config files to be saved in the /home itself.
Am downloading Fedora 13 right now...

Your suggestions, walkthroughs, tutorials, links,... will be greatly appreciated.

---

### Post by portentum on 2010-05-16
> **sunk8 said:**
> Well, I'm tryig something really wicked here...
I love distro-hopping and so have come up with a novel plan...
My parents use Windoze on the primary partition; so I'm dual-booting here. All other partitions are logical drives i.e. parts of an extended partition...
I've installed Ubuntu 10.04 on my PC with /boot and /home on different partitions. This is supposed to be my basic OS...
Now I have about 15 GB free on my extended; so I'm planning to install another distro here (Don't ask me why)... I wanna try Fedora; Mandriva; PCLinuxOS; OpenSUSE; LinuxMint; Gentoo and many more...

So, my question is: Can I use users on my /home partition directly into the other distro? i.e. I don't want to make another user there. And wanna have all config files to be saved in the /home itself.
Am downloading Fedora 13 right now...

Your suggestions, walkthroughs, tutorials, links,... will be greatly appreciated.

Yes, you can. I've used the same /home partition across Fedora, OpenSuse, Gentoo, Debian, Ubuntu, Arch, and possibly others that have now slipped my mind. 

However, you may have permissions issues. I had to chown my home folder back to my user and group after using Fedora and OpenSuse. I suspected at the time that it had to do with SELinux, but I'm not certain and might be wrong there. It could just be a difference in assigning UID and GID? That sounds more likely to me now, and like something that could be fixed with a little research.

Anyway, I don't want to scare you off the idea, it's a great way to keep your settings consistent across distros. Just know that you may have to chown your /home/<user> directory back to yourself.

---

### Post by sunk8 on 2010-05-16
Thanks for your reply...
> **portentum said:**
> Yes, you can. I've used the same /home partition across Fedora, OpenSuse, Gentoo, Debian, Ubuntu, Arch, and possibly others that have now slipped my mind.
Yup, that's precisely what I have in mind.
> **portentum said:**
> However, you may have permissions issues. I had to chown my home folder back to my user and group after using Fedora and OpenSuse. I suspected at the time that it had to do with SELinux, but I'm not certain and might be wrong there. It could just be a difference in assigning UID and GID? That sounds more likely to me now, and like something that could be fixed with a little research.
I'm glad it's possible...
> **portentum said:**
> Anyway, I don't want to scare you off the idea, it's a great way to keep your settings consistent across distros. Just know that you may have to chown your /home/<user> directory back to yourself.
Well, I think it shouldn't be a problem. I'll make a script for the same and introduce it in all distros startup...
What say?

Thanks a ton man... :)

---

### Post by portentum on 2010-05-16
[QUOTE=sunk8]
Well, I think it shouldn't be a problem. I'll make a script for the same and introduce it in all distros startup...
What say?
[/QUOTE]

I think that sounds like a much better plan than anything I might have come up with. The script just needs to run *before* your user tries to log in, otherwise you'll have errors when it tries to access your config files and is unable to. Best of luck with this. I'm no good with scripting, or I'd offer some help with that. :oops:

It just needs to run ```
chown -R <username>:<groupname> /home/<username>
```

---

### Post by sunk8 on 2010-05-16
> **portentum said:**
> I think that sounds like a much better plan than anything I might have come up with.
:guitar:
> **portentum said:**
> The script just needs to run *before* your user tries to log in, otherwise you'll have errors when it tries to access your config files and is unable to. Best of luck with this. I'm no good with scripting, or I'd offer some help with that. :oops:
It just needs to run ```
chown -R <username>:<groupname> /home/<username>
```

Thanks for the code...
My download will be over in a few hours. I'll let you guys know...

---

### Post by mtbsoft on 2010-05-16
Mine is a note of caution.  I once did what you're wanting by accident, though in my case it was across two versions of the same distro.  My problem was that the later version updated some config. files so that the earlier one could no longer make sense of them.

Just keep that in mind when you set things up.

Edit: Damn, beaten to it...!

---

### Post by oldfred on 2010-05-16
It is a lot safer to share /data with just data files. My /home is now only 1GB as I have moved all my data to a different partition. If I want I can copy home settings but do not have to worry about conflicts or permissions.

How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

