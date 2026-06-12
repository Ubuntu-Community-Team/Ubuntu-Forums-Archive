---
title: "Can't rip music cd"
date: 2009-12-01
forum: Desktop Environments
---

### Post by jaime256 on 2009-12-01
Well, I got a music cd that I want to make files out of and this is the error I get when I try to rip it. I'm on Ubuntu 9.04. I have not change any rights on anything myself so I don't know why the system is telling me this. I should note that I just installed the program. I've used it in the past but I don't remember having this problem before.

---

### Post by sgosnell on 2009-12-01
What is the output directory?  If it's not in your /home hierarchy, you'll have to run the ripping program as root, not really a good idea.  Better to redirect to somewhere in you /home directory.  If it can't create the target directory there, you may have to make it yourself beforehand.

---

### Post by jaime256 on 2009-12-01
The program points to the /home/music directory, but I also created a directory in there and on my desktop, both give me the same error still. I did figure it was a rights error, but I think that got changed with the updates since all I have done is install the program. It was working on previous versions as well.

---

### Post by dream_coder on 2009-12-01
Just change the Permissions of the Program for you (the user) either use a terminal and use the 'chown' command for more info type chown --help or chown --man but it normally goes 'sudo chown username path/to/file/filename'

Or 

in a terminal type sudo nautilus find the program right click it then change the owner etc and or just add you to the permissions.

---

### Post by jaime256 on 2009-12-01
Thanks for the info. I just open a terminal and typed, **sudo sound-juicer** to run the program and that let me do what I needed without having to change any rights. Yeah it sucks but at least now I got it working.
I forgot to mention that you have to find out what your program is called first. On the terminal windows you can just type: **locate name of your program**, you can get this from when you open it, it will tell you the name at the top. Once you know it, just add the **sudo** in front of it to run it. Keep in mind that it will put your files in the root folder though.

> **dream_coder said:**
> Just change the Permissions of the Program for you (the user) either use a terminal and use the 'chown' command for more info type chown --help or chown --man but it normally goes 'sudo chown username path/to/file/filename'

Or 

in a terminal type sudo nautilus find the program right click it then change the owner etc and or just add you to the permissions.

---

### Post by oldos2er on 2009-12-01
Check System, Administration, Users & Groups, to see if your user settings include 'Use CD-ROM drives'.

---

### Post by jaime256 on 2009-12-01
Well, you hit right on the first thing I looked at. It's not checked so I checked it, logged out, and it did not work. So I rebooted, and still did not work. So you're right, it's not checked by default now, but it still doesn't work even if you do check it. So that's why I ran it the way I did. I get the same problem on my clean laptop install too. Thank you guys, now I need to get back to my school work. Got all this stuff working so I feel much better. :)

> **oldos2er said:**
> Check System, Administration, Users & Groups, to see if your user settings include 'Use CD-ROM drives'.

---

