---
title: "Linux Crash Tutorial"
date: 2006-09-19
forum: Desktop Environments
---

### Post by doomstone on 2006-09-19
I have been using Linux for a while now, and i like it verry much.
I would put my self as a power windows user, but i linux i still fell a bit lost.

The problems i have.
[LIST][*]What are all the folders in my root dir? (In windows i know that "program files" is where my programs is install, and "Windows" is system files).
[*]I can't seem to get a hang on the file promission system.
[*]I always end up with a lot of packets that i don't use. When i install something to test it, and i don't like it, i unstall it with apt, but alot of packets are no removed. so is there a better way.
[*]What language is most offen used to program linux apps?
[*]Is there a way i can get spell/gramma corection in open office.
[*]What is a good way to partition my harddisks?
[*]What Interface systems are there out there, and witch on shale i use? (Gnome, KDE, Blackbox etc.)
[/LIST]

This is just on the top of my head, but in short, what i realy need to know for me to fell home, is how linux workes.

---

### Post by lagagnon on 2006-09-19
To answer all your questions requires a basic Linux text book or manual. There are tens of those books available for free to borrow at your local library, or there are hundreds of tutorials on the Internet explaining each of your queries in great detail - all you need do is type the keywords into Google - followed by "tutorial" or "HOWTO". 

To answer each of your questions in this forum is folly - there are better resources.

---

### Post by Ramses de Norre on 2006-09-19
1. The folder you know as program files in windows is in linux spread over many folders with each their particular files. Like /bin for binaries, /etc for systemwide settings /doc for manpages, /media and /mnt for mounting, /lost+found for fsck dump, /boot for booting (obvious), /lib for libraries and so on.. Don't wory too much about them though.

2. What do you have difficulties with?

3. Use aptitude instead of apt-get, it removes dependecies when a program is deleted, read [this](http://www.psychocats.net/ubuntu/aptitude) for more info.

4. C, python, bash, C++ ... 

5. Probably but I don't know how.

6. Depends on your needs... I'd advice to have a reasonable big / partition and a bigger /home partition (/home is likes documents and settings in windows).

7. I guess gnome and kde are most used but if you get to know linux better you gan go experiment with others too, it's really fun to do;)
The one you should use depends on your personal taste..

---

### Post by doomstone on 2006-09-19
Thanks for the quick anwser

---

