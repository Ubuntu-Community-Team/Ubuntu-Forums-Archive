---
title: "conky theme problem"
date: 2012-04-02
forum: Desktop Environments
---

### Post by r1nk on 2012-04-02
hey Im using ubuntu 11.10.. i just installed conky and downloaded the conky meet faenza theme.. [http://gnome-look.org/content/show.php?content=133086](http://gnome-look.org/content/show.php?content=133086)

I just followed wat the author said which is copy all the folders in home folder. That all.. Then, i started conky and it only looks like this :-

[[IMG]http://img4.imageshack.us/img4/9049/conkyt.png[/IMG]](http://imageshack.us/photo/my-images/4/conkyt.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

What did i do wrong? :/

---

### Post by brainwash on 2012-04-02
There is a custom script included called .conky-start.sh which you have to run:

```
sh ~/.conky-start.sh
```

---

### Post by r1nk on 2012-04-02
still same.. the conky wont change.. :/

is it bcoz i used gnome 3 prob?

---

### Post by Frogs Hair on 2012-04-02
The start script and some other components of the theme  were hidden when I extracted the theme . I had use Ctrl + H after opening nautilus to view all of the contents of the folder. I have not been able  to get the theme to work on 11.10 so far .

---

### Post by brainwash on 2012-04-02
Well, make sure all files are actually in your home folder:
```
ls -la ~/ | grep .conky
```

Do you get any errors running the script?

---

### Post by r1nk on 2012-04-02
ok i think they r all there right..

```
cj7@cj7-Aspire-4741:~$ ls -la ~/ | grep .conky
drwx------  4 cj7  cj7    4096 2011-09-08 05:19 .conky
-rw-------  1 cj7  cj7    1233 2011-09-08 23:11 .conkyrc-music
-rw-------  1 cj7  cj7    1529 2011-09-08 23:12 .conkyrc-system
-rw-r--r--  1 cj7  cj7    1529 2011-09-08 23:12 .conkyrc-system~
-rw-------  1 cj7  cj7      91 2011-09-08 05:38 .conky-start.sh
cj7@cj7-Aspire-4741:~$ 


```

sorry bcoz this is my 1st time using conky. just wanna make it clear. After extract to the home folder, open terminal and just type "conky" to work it out right?

and when i type the start command in terminal, here wat it wrote..

```
cj7@cj7-Aspire-4741:~$ sh ~/.conky-start.sh
Conky: desktop window (1200024) is subwindow of root window (ae)
Conky: window type - override
Conky: drawing to created window (0x4000001)
Conky: drawing to double buffer
Conky: desktop window (1200024) is subwindow of root window (ae)
Conky: window type - override
Conky: drawing to created window (0x3e00001)
Conky: drawing to double buffer

```

---

### Post by stinkeye on 2012-04-02
The **.conkystart** script has delay of 10 secs so you won't see straight away.

The download contains 2 conky configs which the **.conkystart** script
invokes.A system conky and a music conky.
You can test the system conky with (in terminal)
```
conky -c ~/.conkyrc-system
```

The music conky requires the installation of
conkyexaile, conkybanshee or conkyrhythmbox
depending which music app you use.

To add one of these you need to add the ppa.
The one in the readme is old, see [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=928168") for the developers ppa.

The **~/.conkyrc-music** config is setup for exaile.
Look in the readme for the code for rhythmbox or banshee and edit **~/.conkyrc-music** to reflect your choice.

You can test the music conky with (will only show when your music app is playing)
```
conky -c ~/.conkyrc-music
```


NB***Running "**conky**" in terminal loads the config @ **~/.conkyrc**
     If there is no **~/.conkyrc** config it loads the default config @ **/etc/conky/conky.conf** (which is what you see in your pic)
The -c option tells conky to load a specific config
eg```
conky **-c** ~/.conkyrc-system
```

---

