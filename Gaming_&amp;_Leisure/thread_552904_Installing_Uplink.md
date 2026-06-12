---
title: "Installing Uplink"
date: 2007-09-17
forum: Gaming &amp; Leisure
---

### Post by razumny on 2007-09-17
Ok, I've downloaded the 1.55 version of Uplink, which has provided me with a .sh-file called uplink-complete-1.54DOWNLOAD.sh

I've installed GTK 1.2, using this command: 

```
sudo aptitude install libgtk1.2
```

(By the way, Could I have run this as an apt-get command instead?)

My question is this:

Now what? How do I install using a .sh-file?

---

### Post by lisati on 2007-09-17
Using aptitude for installs suits some situations better because it does some more work on your behalf checking that what you're installing works.

---

### Post by razumny on 2007-09-17
Ok, thanks for that

my question remains; how do I install Uplink using a .sh-file?

---

### Post by glotz on 2007-09-17
You give yourself permissions to execute the file* and then cd into the folder the file is in and type ./filename

man chmod
or use nautilus

should any problems arise, this might be of use [http://ubuntuforums.org/showthread.php?t=154937](http://ubuntuforums.org/showthread.php?t=154937)

---

### Post by razumny on 2007-09-17
I might be stoopeed here, but that gave diddly squat

Mind giving me a step-by-step please?

---

### Post by glotz on 2007-09-17
Sure. Where's the file now?

---

### Post by razumny on 2007-09-17
it's on my desktop

---

### Post by glotz on 2007-09-17
So open the terminal. (=F2 and input gnome-terminal and hit enter) Then 
cd Desktop
chmod 700 filename
and then just
./filename

---

### Post by razumny on 2007-09-17
Thank you

that worked just fine

---

### Post by glotz on 2007-09-17
:)

---

### Post by nefrin on 2008-05-10
I'm having an issue also, I downloaded the .sh file for the game from the website, and made it executable to install. The error I am getting is this:

[I]/home/(user)/.setup7412: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Press Return to close this window...[/I]


The .setup#### file goes up in numbers each time I try to install again. I have tried running apt-get libgtk1.2 and libgtk1.2.so.0 (first worked, second didn't).

Here's what I'm getting for my apt-get (using aptitude here instead):
[I]
>sudo aptitude install libgtk1.2.so.0
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree... 50%
Building dependency tree       
Reading state information... Done
Initializing package states... 0%
Initializing package states... 56%
Initializing package states... Done
Building tag database... 0%        
Building tag database... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/I]

Any help on this?

---

### Post by Perfect Storm on 2008-05-11
You need to close synaptic or add/remove. You can only use the repo. from one application at the time.

---

### Post by manco1911 on 2008-06-28
thanks man, i was looking for this. every day im more thankfull for this forum. 

home someday i can give a helpfull post.


by the way, how do i qualify a post ? for example for giving this thread an A+ ?

---

