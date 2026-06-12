---
title: "ubuntu/vista dual boot dell 9400"
date: 2007-10-14
forum: Dell  Ubuntu Support
---

### Post by yoramspreij on 2007-10-14
dear readers,

i wasn't sure where i had to post this so i picked the dell sub cause i have a dell 9400.
my problem is that i wanted to install ubuntu to learn more about this operating system.
i had vista on my laptop, and a friend gave me the ubuntu live cd (feisty fawn edition thingy). the installation cost me about 3 hours cause i was too afraid to partition and lose my vista, finally i found another person who used ubuntu and she helped me. well everything worked fine.
grub just forwarded to vista unless i pressed esc in 3 sec's and select ubuntu. i didn't really like that so i asked if i could get vista in the menu so i wouldn't have to press esc first... well she filled my grub menu lst with the required info so that it would work. it gave an error. at that time someone else apeared and told us that he had had the same problem and installed lilo to fix it. well we tried that but now i can't get to my vista. i've tried to inplement it in the lilo conf but it doesn't work (i did compile it) so what i wanted to do is go back the the esc part, cause that worked. but now i can't uninstall lilo, i tried typing lilo -u and other variations in the terminal but it gives me "permission denied"
could someone please help me, i really need my vista because i need to start working on my php asignment( yes i know ubuntu can do that too but i'm almost finished on my vista part)

ps. i tried the vista install cd for recovery but it couldn't find my vista partition:confused::(

Greetz

Yoram

---

### Post by stingx on 2007-10-15
First of all you should check, that your Vista NTFS partition still exists. 
You can check it various ways, for example, if you know label of your ntfs partition, try
$  ls -l /dev/disk/by-label/
Remember symbolic link destination (e.g /dev/sda1) and execute
$ ls -l /dev/disk/by-uuid/
Find entry with link destination as in first command, write down UUID (for example, my 12B2EE276DBAEB51)

This UUID used to unique identify the partion.

Then, modify /boot/grub/menu.lst for example with gedit
$ sudo gedit /boot/grub/menu.lst

First, comment out line, where "hiddenmenu" option appears. This should look like:

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

Then, add to the end of file this lines (if similar line exists, just edit it content)
title		Windows
root		(hd0,2)
savedefault
makeactive
chainloader	+1

Change in (hd0,2) second number 2 to your own. It is calculated from device name, you found in the first step minus 1. For example, if device is /dev/sda1, then it root will be (hd0,0), if /dev/sda5, then (hd0,4), if /dev/sdb3 then (hd1,2), and so on...

Now, to restore grub in boot sector use
$ grub-install /dev/sda

Have fun!

---

