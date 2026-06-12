---
title: "Could not look up internet address"
date: 2005-12-27
forum: Desktop Environments
---

### Post by ltb0ngo on 2005-12-27
First time really using linux but I know all my hardware works with ubuntu because I tried the live cd. I've installed it in a duel boot with xp but when I type in my username and password I log in fine but something happens before I get to the desktop. This little box pops up which says:

"could not look up internet address for "my computers name". This will prevent GNOME from operating correctly. It may be possible to correct the probelm by adding "my computers name" to the file /etc/hosts."

How do I fix this probelm and can you please explain in baby steps to make sure I get it:razz: . Also I can't access any of the admin bits like network for some reason is this normal because I could on the live cd and if it is normal how do I access them?

---

### Post by stevea1210 on 2005-12-27
Can we please see the contents of your /etc/hosts file.

To do that. open a terminal (applications, accessories, terminal)
than type ```
cat /etc/hosts
```

Copy the output and paste it into a reply.

---

### Post by ltb0ngo on 2005-12-27
Thanks for the baby steps the contents are 127.0.0.1 localhost and thats it

---

### Post by stevea1210 on 2005-12-27
Let's modify that.  It should have your computers name in it, possibly some other info as well.

Go back to the terminal, type ```
sudo gedit /etc/hosts
```
hit enter and you will be prompted for your password.  after that, gedit (similar to notepad in MS) will open the file.

change the line to 

```
127.0.0.1 localhost.localdomain  localhost  *your computers name*
```
Then save the file.  I would then suggest a reboot, and to try it again.  Let me know if that works.

edit - don't put your computers name inside of **.  that was just to set that off.  Just type the name in.

---

### Post by ltb0ngo on 2005-12-27
OK i pasted in sudo gedit /etc/hosts and pressed enter and this came up 
sudo: unable to lookup *my computers name* via gethostbyname()

---

### Post by harisund on 2005-12-27
Wow ! What a coincidence. I had the exact same problems too.

I will tell you what I did. During internet testing stage of the install, it said 
"My host is either not using the DHCP protocol or the DHCP server is real slow". I then hit "Go Back" and went directly to the next stage of the install, which was "Multiseat system." It never asked me the hostname, and instead directly went to the partitioner and carried on. 

If I were you right now, I would do a complete reinstall instead. Start from scratch. Ideally, Ubuntu installer should ask you for hostname immediately after the internet configuration stage. If it doesn't go back and make sure it does. 

And tell back here whether it worked. For me it did.

---

### Post by stevea1210 on 2005-12-27
Re-install is definitely an option.  I have two others you could try.

1) boot into recovery mode.  to do this, hit ESC as your pc starts to boot up.  You will be greeted with a list of options to boot.  One of them will end in recovery mode.  Highlight that option, and hit enter.  When booted up, try the same set of instructions again.

2)Use a live cd, such as knoppix, slax, or the ubuntu live cd.  Boot the computer using that.  When you get to the gui, you should be able to modify the file that way.  You won't need to use "sudo" if you are using slax, or knoppix.

---

### Post by ltb0ngo on 2005-12-28
Ok i tried the recovery mode and it came up the same as it did in normal so no help. I then reinstalled ubuntu only to find that the probelm was still there. I then followed stevea1210s advice and used a live cd (slax) and changed it to what he said and it worked perfectly. So thanks a lot stevea1210 and harisund don't no why reinstalling didn't work but there we go.:KS

---

### Post by stevea1210 on 2005-12-29
Glad I could help :)

---

### Post by 504harry on 2005-12-31
[QUOTE=stevea1210]Let's modify that.  It should have your computers name in it, possibly some other info as well.

Go back to the terminal, type ```
sudo gedit /etc/hosts
```
hit enter and you will be prompted for your password.  after that, gedit (similar to notepad in MS) will open the file.

change the line to 

```
127.0.0.1 localhost.localdomain  localhost  *your computers name*
```
Then save the file.  I would then suggest a reboot, and to try it again.  Let me know if that works.

edit - don't put your computers name inside of **.  that was just to set that off.  Just type the name in.[/QUOTE]

Hi there, I have a similar problem and answers here are slightly different - this thread seems to have fixed it - could I ask those involved to look up their /etc/host file and report what's there with the PC working correctly.......mine says "ubuntu" no dotcom or IP numbers - no wonder Gnome is a bit displeased. 

I woukd prefer not to re-install, although this would have been a lot quicker [if it fixes it] - but I want to learn what is wrong....I guess.

[[Whilst many installations will be done with internet  connection, some won't - or we upgrade the PC - why doesn't there exist a sensible "up-date hardware and connections" - which should overcome such situations? Usefully it could guide us through the key external links that PC's have from time-to-time.
]]

/
Please also read my 31Dec05 post covering "my story so far" on ****Clean Install**** thread - thanks

---

### Post by ltb0ngo on 2006-01-01
My /etc/hosts file now reads "127.0.0.1 localhost.localdomain localhost *my computers name*" Hope that helps:p

---

