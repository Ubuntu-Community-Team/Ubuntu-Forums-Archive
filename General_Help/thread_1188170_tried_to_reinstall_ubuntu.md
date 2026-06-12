---
title: "tried to reinstall ubuntu"
date: 2009-06-15
forum: General Help
---

### Post by xlh1000 on 2009-06-15
I recently tried to reinstall ubuntu 8.04.1 LTS but got different results this time.
Instead of going through all the regular sequences after initial install, it stopped at a black screen this time and it shows the command 'grub-' and wants me to type something, but i don't know what. It says to use 'tab' to see a list of possible commands.
Why did it go this way this time and what do i do now to fix it? I used the 'install inside of windows' option, but i cannot even remove it in 'add/remove' in control panel.

---

### Post by c1rcu1t on 2009-06-15
Were you trying to dual-boot?

---

### Post by xlh1000 on 2009-06-15
Yes.

 I installed it before like this with no problems, but removed it because i can not get a dial-up internet connection to work.

It did not go through all the system checks during this install and does not bring me to the ubuntu desktop.

---

### Post by c1rcu1t on 2009-06-16
Check out this link, if you haven't already been here, to effectively understand and execute a dual-boot for Ubuntu and Windows XP. 

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

If you are attempting to set up a dual-boot with a version other than XP, check out this link. Be cautious though; achieving this setup is a bit more difficult than with XP, as Vista likes to automate things for it's users. :(  At the top of the page you can select from the drop-down menu which OS was installed first, so that you can be sure you are getting the correct instructions. 

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2)

I have found that with setting up mulitple partitions on one drive, it is typically easier to use a third party program such as GParted, versus using disk management tools inside Windows to resize said partitions. Some users will find this option more difficult or confusing, but at least it's another alternative if for some reason you can't get it working the other way. I will admit that using programs like GParted take a significant amount of time to resize partitions, especially when the overall size of the disk exceeds capacities of 40 GB, so be patient. Here is the link to all stable versions currently listed for GParted if you are interested. 

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

If for some reason you're having trouble accessing GRUB or any other bootloader after installing either OS, you can recover the selection option through another Live CD called SuperGRUB. 

[http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

Hope this helps. Remember, be patient, as we all know that good things come to those who wait.

---

### Post by xlh1000 on 2009-06-17
Thank you c1rcu1t.
In the mean time, i tried something else.
I remembered that i copied the last install to my E: drive.
So what i did was to overwrite the files on my C: drive with the old install.
However, it would not accept my user name or password, but it did allow me at this point to uninstall it from the C: drive and perform a fresh install. Everything is fine now, except for the initial reason for removing it in the past.
I have tried over and over to get dial-up to work to no avail.
I have tried all the instructions on this forum and others on Google with no luck.
The problem i keep running into is that no matter what commands i type from the instructions, it tells me things like 'file not found' or 'you don't have permission to access that file' or things like that.
Is there an initial set-up phase after install where i can actually access this stuff? 'Sudo' commands or 'Superuser'?

Thank you

---

### Post by zvacet on 2009-06-17
> file not found

That means that you are not in same directory with package you are trying to install.For example,when you open terminal you are in home directory.If package you want to install is on Desktop and you aretrying to install it likr it is in home  you will get this message.You can solve this easy way.Only thing you have to do is to type

```
cd Desktop
```

Now you are in same directory where file is ansd you can install it.

> you don't have permission to access that file

use **sudo **in front of command.

---

### Post by c1rcu1t on 2009-06-18
Sorry for the delayed response, I've been working too many hours lately. I was going to mention the same as zvacet. Getting used to typing in the terminal takes some time. I still forget a **sudo** here and a **cd **there. Just remember that sudo stands for super-user do. I'm sorry I can't be of any assistance when it comes to a dial-up connection with your recent installation though, as I haven't used dial-up in some years, and even then it was on a Micros*** system. Hopefully like everything else you'll find a solution. Just keep at it. Bestof luck though![URL="http://ubuntuforums.org/member.php?u=79320"]
[/URL]

---

### Post by xlh1000 on 2009-06-19
Thank you zvacet and c1rcu1t.
This is very helpful about the commands and terminal. Now maybe i can get somewhere. I have been under the impression from other things i have read that 'sudo' is the quickest way to bork something up if you don't know what you are doing, so i didn't use it. And i am sure it is, but what good are the key's if they don't fit the lock, right?  (in reference to file not found, ect;) 

As far as the modem, i am just going to put in a US Robotics/3Com that is known to work.
Thank you zvacet and c1rcu1t for the bump in the right direction.

---

### Post by c1rcu1t on 2009-06-19
Glad to be of service. I was also going to suggest something along the lines of a USB Wifi dongle to use instead. What with the majority of residential neighborhoods and areas already offering wireless, even open access to some. But either way, it seems you're on the right track to achieving results. Just as a last note, if you're interested, a friend of mine emailed me this link to 10 free Linux e-books on a very popular website that posts a number of interesting articles and tutorials for Linux users of all flavors. The link is below. Even if you're only interested in one or two of them, I've always been of the opinion that 'free is for me' which of course is extended to the understanding of open-source software. I would also suggest searching for torrents of e-books, as you would be surprised what is available to expand your knowledge in any area, most importantly in the world of computers and technology. I would give you direct links to such sites although, I am unsure as to the policies or opinions of the Ubuntuforums staff, and would rather keep a clean slate than anything. Regardless, best of luck with your endeavors. 

[http://www.linuxhaxor.net/2009/05/10/10-free-linux-ebooks-for-beginners/](http://www.linuxhaxor.net/2009/05/10/10-free-linux-ebooks-for-beginners/)

---

