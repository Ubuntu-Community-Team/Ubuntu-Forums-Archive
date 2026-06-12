---
title: "Mozilla Firefox 1.5"
date: 2005-12-01
forum: Desktop Environments
---

### Post by sjpritch25 on 2005-12-01
How do i get Mozilla Firefox 1.5????  do i have to use apt-get.  I tried, but i don't know the correct command.  This didn't work " sudo apt-get mozilla-firefox update".  :)

---

### Post by frodon on 2005-12-01
[https://wiki.ubuntu.com/FirefoxNewVersion?](https://wiki.ubuntu.com/FirefoxNewVersion?)

enjoy ;)

---

### Post by kperkins on 2005-12-01
That's because 1.5 isn't in Ubuntu repositories. And it won't be.  It may get backported at some time (there's a thread in the backports forum, somewhere, about it) or you can download the source archive from mozilla.com (wow, that seems wierd to say) and install it locally (like in your /home folder).

---

### Post by sjpritch25 on 2005-12-01
I used the instructions in wiki.  They worked except for the fact the when i "typed firefox in the terminal" it opened firefox in version 1.07 :( 
Also, I recieved these messages in the terminal
> stefan@breezybadger:~$ firefox
LoadPlugin: failed to initialize shared library libXt.so [libXt.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library libXext.so [libXext.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library /usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so [/usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so: undefined symbol: XtCalloc]
*** loading the extensions datasource
LoadPlugin: failed to initialize shared library /usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so [/usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so: undefined symbol: XtCalloc]
*** loading the extensions datasource


I went into /opt/firefox   and i clicked on the firefox shell script.
I recieved a warning about some globel confirmation and firefox 1.5 opened.  
Any guesses on why i had these problems.  I am new to linux.  I am pretty sure i typed everything in correctly.

---

### Post by sjpritch25 on 2005-12-01
Java isn't working either

---

### Post by swmiller6 on 2005-12-14
I am using the instructions from the wiki and I get the following message after I type firefox in the comandline:

/opt/firefox/run-mozilla.sh: line 131: 15882 Floating point exception"$prog" ${1+"$@"}

Anybody know how to fix this?

---

### Post by commodore on 2005-12-16
Seems nothing useful is working on Ubuntu/Linux.

---

### Post by Rackerz on 2005-12-16
[QUOTE=commodore]Seems nothing useful is working on Ubuntu/Linux.[/QUOTE]

Well an attitude like that wont get Firefox 1.5 working, will it?

Use this [http://ubuntuforums.org/showthread.php?t=99004&highlight=installer+script](http://ubuntuforums.org/showthread.php?t=99004&highlight=installer+script) to install Firefox 1.5, it does everything automatically for you.

---

### Post by commodore on 2005-12-16
I tried installing it by the wiki but I can't understand this:
cd ~/Desktop/ffsettings
 mv * ~/.mozilla/firefox/*.default

and the script doesn't work.

How hard can installing firefox be??

---

### Post by jrib on 2005-12-16
[QUOTE=commodore]I tried installing it by the wiki but I can't understand this:
cd ~/Desktop/ffsettings
 mv * ~/.mozilla/firefox/*.default

and the script doesn't work.

How hard can installing firefox be??[/QUOTE]

Those are the commands to restore your settings (from firefox 1.07), as the wiki explains.  You created the backup with the first step in the wiki.  You enter them in a terminal (Applications menu -> Accessories -> Terminal).  

I think you should go through a CLI (command line interface) tutorial before you try to install firefox1.5.  You shouldn't be doing it if you don't understand what each command means.  Here is a good one to go through: [http://www.linuxcommand.org/](http://www.linuxcommand.org/) .  If you take the time to go through it now, you'll feel more comfortable with everything you do from then on.  Good luck.

---

### Post by commodore on 2005-12-17
I do understand what the commands mean and I have used the terminal a lot before. I just don't understand what does he want from me with those * marks. I think I have to type some directory in my home there, but I'm not sure.

I have another way of backing up so I don't need help anymore.

---

### Post by Rackerz on 2005-12-17
Like i said, you don't need to go through the difficult steps of the wiki, use this instead;

[http://ubuntuforums.org/showthread.php?t=99004&highlight=installer+script](http://ubuntuforums.org/showthread.php?t=99004&highlight=installer+script)

But if your learning to use CLI i suggest using the wiki.

---

### Post by richie.r on 2005-12-17
[QUOTE=_jason]Those are the commands to restore your settings (from firefox 1.07), as the wiki explains.  You created the backup with the first step in the wiki.  You enter them in a terminal (Applications menu -> Accessories -> Terminal).  

I think you should go through a CLI (command line interface) tutorial before you try to install firefox1.5.  You shouldn't be doing it if you don't understand what each command means.  Here is a good one to go through: [http://www.linuxcommand.org/](http://www.linuxcommand.org/) .  If you take the time to go through it now, you'll feel more comfortable with everything you do from then on.  Good luck.[/QUOTE]

Hi guys, I'm a newb, I followed the the wiki and had no problems but I made sure I had done a full ubuntu update beforehand, and because I had a new install of ubuntu I did not worry about copying any bookmarks etc.

---

### Post by syklitengutt on 2005-12-17
I used the installer script, and for the first time ff1.5 is working,
and almoust all my plugins work.

But I cant get my java plugin to work.
On my comp the libjavaplugin_oji.so is in
usr/lib/j2re1.5-sun I think.

I tried to make a link to shared lib in the FF pluginfolder but it didnt work.

any ideas?

---

### Post by jrib on 2005-12-17
[QUOTE=commodore]I do understand what the commands mean and I have used the terminal a lot before. I just don't understand what does he want from me with those * marks. I think I have to type some directory in my home there, but I'm not sure.

I have another way of backing up so I don't need help anymore.[/QUOTE]

```

cd ~/Desktop/ffsettings
mv * ~/.mozilla/firefox/*.default

```

You're suppose to just put the '*' in your command.  The shell will expand it to match all of the possible filenames depending on where the '*' shows up. 

 So here, you will be moving every file in ~/Desktop/ffsettings to every folder in ~/.mozilla/firefox that ends with '.default'.  But firefox will just make one folder with .default (your default profile strangely enough :P).  The reason for the asterisk in that last part is that firefox will put random characters there for every user.  The asterisk takes care of that.

You can see what it does, very easily.  Try these commands:
```

cd ~/Desktop/ffsettings
echo *
echo ~/.mozilla/firefox/*.default

```

See [http://www.linuxcommand.org/lts0050.php#wildcards](http://www.linuxcommand.org/lts0050.php#wildcards) for more info, they are really useful.  Glad you figured it out.

---

### Post by jrib on 2005-12-17
[QUOTE=syklitengutt]I used the installer script, and for the first time ff1.5 is working,
and almoust all my plugins work.

But I cant get my java plugin to work.
On my comp the libjavaplugin_oji.so is in
usr/lib/j2re1.5-sun I think.

I tried to make a link to shared lib in the FF pluginfolder but it didnt work.

any ideas?[/QUOTE]

If you read the thread where the installer script is, there are several people that had the same problem and arnieboy helps them out.  Maybe the same method will work for you.

---

