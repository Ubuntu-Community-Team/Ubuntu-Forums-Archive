---
title: "different color terminal for SSH"
date: 2009-05-15
forum: General Help
---

### Post by pjones0404 on 2009-05-15
I have a few machines that I SSH into on occasion. I would like to know if there is a way to have the terminal to be color coded based on the machine i am connected to. 

For example... i would like the terminal to be black on the local machine. When i connect to machine #1 i would to have a blue terminal and when connected to machine #2 it would be red. this way when i have 3 terminals open i am able to easily determine which one is connected to what machine. 

is this possible?

---

### Post by trwww on 2009-05-15
Check out screen, theres really not much you can't do with it.

The syntax for .screenrc is pretty cryptic. To get mine the way I wanted, I hopped around a couple IRC channels asking questions eventually finding a helpful screen expert.

---

### Post by pjones0404 on 2009-05-15
i appreciate the quick response. I googled around a bit for screenrc and am confused as to what it actually is. If anyone could give a breif explanation as to what it does i would appreciate it. 

I will continue to look for screenrc as well as how to set this up i am just happy that it looks like it is possiblei just have to determine exactly what i need to do to accomplish it.

---

### Post by Bark on 2009-05-16
> **pjones0404 said:**
> I have a few machines that I SSH into on occasion. I would like to know if there is a way to have the terminal to be color coded based on the machine i am connected to. 

For example... i would like the terminal to be black on the local machine. When i connect to machine #1 i would to have a blue terminal and when connected to machine #2 it would be red. this way when i have 3 terminals open i am able to easily determine which one is connected to what machine. 

is this possible?

See

[http://stackoverflow.com/questions/263892/change-the-background-color-in-gnome-terminal-through-a-command](http://stackoverflow.com/questions/263892/change-the-background-color-in-gnome-terminal-through-a-command)

---

### Post by CatKiller on 2009-05-16
You could probably do this by editing the ~/.bashrc on each computer. So machine #1 would display blue and machine #2 would display red (locally and over SSH). Unfortunately, I don't know anything about the options for that file, so I can't give you specific guidance. You should be able to find some bashrc display options though.

---

