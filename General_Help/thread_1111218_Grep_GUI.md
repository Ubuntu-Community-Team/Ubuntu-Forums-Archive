---
title: "Grep GUI?"
date: 2009-03-30
forum: General Help
---

### Post by codeseer on 2009-03-30
I'm still partially in the transition phase from Vista to Ubuntu. One of the types of software I have been unable to find a replacement for is a graphical grep application. I use the command line grep for common tasks, but I have some specialized tasks where I need to search multiple files quickly and repeatedly, for different phrases and there's a great possibility that a lot of results will be returned; this makes the command line grep less a viable option in my case.

In Windows, I used these:

[http://code.google.com/p/dngrep/](http://code.google.com/p/dngrep/)
[http://www.wingrep.com/](http://www.wingrep.com/)

My searching has failed; so, I ask if, by experience, any of you might know of a good replacement?

(I hope this is the correct area to post.)

---

### Post by issih on 2009-03-30
Neither of them look exactly featureful, but I found these two:

[http://sethoscope.net/grepui/](http://sethoscope.net/grepui/)

[http://sourceforge.net/projects/jgrep/](http://sourceforge.net/projects/jgrep/)

They might be in the repositories if you poke around.

Hope that helps

Edit..one that definitely is in the repositories, and looks pretty good is searchmonkey....

---

### Post by codeseer on 2009-03-30
> **issih said:**
> Neither of them look exactly featureful, but I found these two:

[http://sethoscope.net/grepui/](http://sethoscope.net/grepui/)

[http://sourceforge.net/projects/jgrep/](http://sourceforge.net/projects/jgrep/)

They might be in the repositories if you poke around.

Hope that helps

I did run across the grepui, but it only searches one file at a time and as you said, it is seriously lacking in features. The jgrep download seems to be corrupt to me, but from the screenshot it looks to only support one file also.

I tried wine with dnGrep and got that error: GdipCreateFontFamilyFromName
There's probably no easy way around that one.

---

### Post by kaivalagi on 2009-03-30
Try "searchmonkey" as issih suggested in his edit

it works like a charm, should cater for all your requirements

---

### Post by Locutus_of_Borg on 2009-03-30
you shouldnt need a GUI for grep..

```

for file in `grep hello -lR /home`; do sed -e "s/hello/goodbye/ig" $file > /tmp/temp.file && mv /tmp/temp.file $file; done
```

looks to do the same as dngrep. e.g. search all files recursively in any given directory for a word or phrase, and replace that word/phrase with another (above example will change any instance of the word "hello" in every file within /home to the word "goodbye")

you could also simply generate a file listing of all files that contain a given string of text

but that's just me, and i hate needless GUI's

---

### Post by codeseer on 2009-03-30
> **Locutus_of_Borg said:**
> you shouldnt need a GUI for grep..

```

for file in `grep hello -lR /home`; do sed -e "s/hello/goodbye/ig" $file > /tmp/temp.file && mv /tmp/temp.file $file; done
```

looks to do the same as dngrep. e.g. search all files recursively in any given directory for a word or phrase, and replace that word/phrase with another (above example will change any instance of the word "hello" in every file within /home to the word "goodbye")

you could also simply generate a file listing of all files that contain a given string of text

but that's just me, and i hate needless GUI's

A GUI is just so much faster in this particular context that I'm using it. It's faster to double click a textbox, type a new phrase in and hit enter, than to hit the Up arrow key, then the Left arrow key several times, then the Delete key several times and finally type a new phrase in.

**SearchMonkey does the trick. Thank you both very much!**

---

### Post by Locutus_of_Borg on 2009-03-30
faster shmaster :P

point taken, but well, now you can do that if X wont start for some reason... :)

---

### Post by kanikilu on 2009-03-30
I'm not sure if this will do what you are looking for, but in my search (no pun intended) for a program that would do "Search & Replace in Files", I found [regexxer](http://packages.ubuntu.com/intrepid/regexxer), which fits the bill...

---

### Post by codeseer on 2009-03-31
I should note here that SearchMonkey does work well and serves my purpose. However, it crashes fairly often when clicking the search button or clicking on a result. If someone else comes along looking for a Grep GUI, please be aware of this issue; it seems there was a bug report filed on it over 2 years ago and it's doubtful that the bug will be fixed.

On a side note...If anybody discovers some other application that serves the purpose, please let me know.

---

### Post by magmax on 2009-09-03
Hi there.

I had the same problem: I couldn't find a good grep GUI. So, I wrote mine.

It has been without modifications about 1 year. This does not mean it is perfect... This mean that it has only one user: me.

Well... really it has two engines: pygrep engine and grep engine. both of them have advantages.

It is called "Pygrep" and is made in python. I recomend to use the SVN version, since it has a year of development more than the package. It is made in python, so you have to compile nothing.

You can find screenshots and the program in the web of [Pygrep, the grep gui in python]("http://sites.google.com/site/magmax9/projects-1/pygrep").

Please, feedback is welcome.

---

### Post by Rytron on 2009-09-05
> **magmax said:**
> Hi there.

I had the same problem: I couldn't find a good grep GUI. So, I wrote mine.

It has been without modifications about 1 year. This does not mean it is perfect... This mean that it has only one user: me.

Well... really it has two engines: pygrep engine and grep engine. both of them have advantages.

It is called "Pygrep" and is made in python. I recomend to use the SVN version, since it has a year of development more than the package. It is made in python, so you have to compile nothing.

You can find screenshots and the program in the web of [Pygrep, the grep gui in python]("http://sites.google.com/site/magmax9/projects-1/pygrep").

Please, feedback is welcome.

Hi magmax
I downloaded [http://mirrors.linhub.com/savannah/pygrep/pygrep_1.0.0.tgz](http://mirrors.linhub.com/savannah/pygrep/pygrep_1.0.0.tgz)
How exactly do I install it though?

I have put this into the INSTALL file
```
#!/bin/bash
/home/rytron/Desktop/pygrep_1.0.0/pygrep.py
```

---

### Post by magmax on 2009-09-09
Well... The package is not too much maintained...

try this:
~/Desktop$ cvs -z3 -d:pserver:anonymous@cvs.savannah.nongnu.org:/sources/pygrep co pygrep

I think you can try it directly: only enter the directory and execute it:
~/Desktop/pygrep.py

Then, you can create a file (for example, 'pygrep') with this content:
#!/bin/bash
~/Desktop/pygrep.py

Change the permissions (700, for example, with $chmod 700 pygrep) and try it to execute pygrep directly. It is important to execute it from the main pygrep directory, in order to allow pygrep to find all their files.

If you have any trouble, please, mail me (my address is in my web page or in the main [pygrep, the python Grep GUI]("http://sites.google.com/site/magmax9/projects-1/pygrep") web).

Thank you!

---

### Post by magmax on 2009-09-09
Hi again.

I found a screencast I saved some time ago. It is here: [screencast of pygrep, the python grep GUI]("http://sites.google.com/site/magmax9es/projects-1/pygrep/screencast1.avi?attredirects=0").

It has no sound, but shows next:
[LIST=1]
[*]how to create a new profile.
[*]how to configure a profile against pygrep code.
[*]how to search.
[*]how to search showing more than one row.
[/LIST]

I tought it can like you.

---

### Post by Rytron on 2009-09-09
Thank you magmax. I will try your instructions. :)

---

### Post by netkeeper on 2010-01-20
pygrep is a nice prog , thx :D

---

### Post by Rytron on 2010-01-20
I now use Searchmonkey. You can get it in the Synaptic package manager.

---

### Post by magmax on 2010-05-12
> **Rytron said:**
> I now use Searchmonkey. You can get it in the Synaptic package manager.

Hmmmm... I tried SearchMonkey and it looks fine.

It has a huge advantage: it is debian package :-D But I don't like the interface. 

I was speaking with authors and they say that they are re-making it with QT. Maybe second version is better than first one.

Because of this, I began to change my *[grep gui in python, called pygrep]("http://www.magmax.org/drupal/pygrep")* and I created the third version of it.

It is a bit unstable by now, but I think that it can grow in a very good way. The help of the program (in the site) says how to use it and shows all the program screenshots.

I am trying to make pygrep as an alternative to searchmonkey. So, you can choose.

I am working in make a debian package from pygrep too.

Maybe you can find it interesting. 

Thank you!

---

### Post by Rytron on 2010-05-12
> **magmax said:**
> Hmmmm... I tried SearchMonkey and it looks fine.

It has a huge advantage: it is debian package :-D But I don't like the interface. 

I was speaking with authors and they say that they are re-making it with QT. Maybe second version is better than first one.

Because of this, I began to change my *[grep gui in python, called pygrep]("http://www.magmax.org/drupal/pygrep")* and I created the third version of it.

It is a bit unstable by now, but I think that it can grow in a very good way. The help of the program (in the site) says how to use it and shows all the program screenshots.

I am trying to make pygrep as an alternative to searchmonkey. So, you can choose.

I am working in make a debian package from pygrep too.

Maybe you can find it interesting. 

Thank you!

Hello magmax. Yes, that sounds interesting. I also use recoll now.
sudo apt-get install recoll

:)

---

### Post by mattalexx on 2010-10-01
> **codeseer said:**
> Grep GUI?

I'll answer a question with a question. Why?

> **codeseer said:**
> I use the command line grep for common tasks, but I have some specialized tasks where I need to search multiple files quickly and repeatedly, for different phrases and there's a great possibility that a lot of results will be returned; this makes the command line grep less a viable option in my case.

Check out the [less command]("http://linux.about.com/library/cmd/blcmdl1_less.htm")

---

### Post by kaivalagi on 2010-10-01
> **mattalexx said:**
> Check out the [less command]("http://linux.about.com/library/cmd/blcmdl1_less.htm")

And if the file is 1000 screens of text you still expect less will suffice?

Old thread anyway, I'd half expect you're looking for an argument, but I'm stopping here :P

---

### Post by martin_lindhe on 2012-02-15
I have been looking for a visual grep tool aswell for a while. I have been using sagasu, which works fine for the task but lacks in features & is unmaintained.

  sudo apt-get install sagasu

I tried searchmonkey, it crashes frequently, had troubles opening files with found line
recoll pulls in half of Qt on a slim xfce setup, and is wierd to use
the pygrep mentioned in this thread seems to have disappeared (website links & cvs is dead)

---

### Post by oldos2er on 2012-02-15
Closed, necromancy.

---

