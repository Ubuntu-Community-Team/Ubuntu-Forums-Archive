---
title: "Still Can't get rid of nero - HELP please!"
date: 2009-04-01
forum: General Help
---

### Post by LawC on 2009-04-01
Hey all:
   I'm on ubuntu 8.10, I installed nero linux 3.5.1.0 and now I want to uninstall it (it kinda blows). I followed advice elseware on the unbutu formus and none of those methods worked. It is nowhere to be found in synaptic. The command line thing "sudo apt-get remove --purge ???" does not work either. 
I get something like "E: Couldn't find package ???" - where ??? is many different things i've tried including exactly what I got form other peoples advice.

I think the command line thing would work if I just knew the exact name of it. I tried lots of variations that seemed to make sense and no luck.
Nothing in the docs or in the homepage. Anyone got any suggestions?

Thanx in advance!

---

### Post by 3Miro on 2009-04-01
There are multiple ways to install stuff in ubuntu and unless you used a .deb package, you will not find it in dpkg

Sometime applications run their own install scripts and put their stuff in folders of their choosing. First check to see i Nero  itself has and uninstall script. Find the Nero folders and look around for uninstall or maybe README with instructions or something like that.

If they don't have such thing, then the big question is: did  nero put some driver and/or some kernel module or anything else in place it was not supposed to. If the answer is no, then you can remove the nero folder and then go to /usr/bin and look for links to nero files and remove those as well.
```

cd /usr/bin
ls -al | grep nero

```
would list all nero stuff in the folder and if it looks like:
```

-rwx--------  someowner:somegroup random stuff nero -> '/somefolder/nerofolder

```
then you can remove it (post the output of the first two commands if you are in doubt.

At the end you might have to remove nero's entries from the menu and file associations (System -> Prefs -> Preferred Apps.)

If Nero has installed more crap, I don't know what to do. I don't want to mess with kernel modules and such.

---

### Post by anjilslaire on 2009-04-01
Ok, I downloaded & installed the nerolinux trial, just to see how this is done.
It is a bit nasty, I might add. I used Nero 5/6 back in th day on Windows, but once I found k3b on linux, I never looked back.

Remove it with this:
```

sudo apt-get purge nero*

```

Edit: This is assuming you were smart and installed it via the Nero-supplied .deb file. Strange that it's not listed in synaptic, even via a deb...

---

### Post by markharding557 on 2009-04-01
i think the motto is always use a .deb if possible and for any one else who wants this program,it does have one on aheads site.
you could search for all the bits and get rid that way but be very careful if you do.
if you want to play safe then remove the menu entries and ignore it

---

### Post by leonardo_neo on 2009-04-01
> Ok, I downloaded & installed the nerolinux trial, just to see how this is done.

1+

Kudos! A real helping spirit!! :)

---

### Post by LawC on 2009-04-01
Aparently I've gotten myself in quite a pickle here!
I searched my filesystem for "nero" with nautilus and got lots of files. Something tells me I should not remove them??? If I removed them to the trash I suppose I could put 'em back later. There is no uninstall anywhere. There's docs but no uninstall in there either.

I think I can now agree with markharding when he wrote "i think the motto is always use a .deb if possible..."
Hummm. Lesson learned! Here's how I installed if that helps...
"tar xzvf nerolinux-3.5.1.0.tgz -C /"

If I had checkinstall installed - would that have helped me out here. If so, how do you use it? (I have it now 'cause I found it while reading other threads on uninstalling nero)

Well I guess I'll wait around for a while and see if someone has a good fix. Otherwise I'll try to zap all those files in the nautilus search.... If that doesn't work, I'll just remove it from the menus and forget about it. 

Thanks for everyones help...

---

### Post by rattking on 2009-04-01
Hi 
could you reinstall the tgz using the checkinstall method then remove the resulting deb that checkinstall made?
or another way
use alien to convert the .tgz into a .deb then force install the deb and remove it with apt-get remove --purge?

---

### Post by LawC on 2009-04-01
> Hi 
could you reinstall the tgz using the checkinstall method then remove the resulting deb that checkinstall made?
or another way
use alien to convert the .tgz into a .deb then force install the deb and remove it with apt-get remove --purge?

Thanks. That sounds like it might work. Only problem is I have no idea how to use either checkinstall or alien. Would someone be kind enough to explain one of those methods to me (the easiest one!). My experience level is low so I need some code! I did get checkinstall, and I still don't know how to use it, but I thought you use it before you install .tgz (I'd like to see some code on how to do that too, just so this doesn't happen again.)

Thanks a million. This community rocks!

---

### Post by theozzlives on 2009-04-01
```
sudo apt-get install alien
```
```
sudo alien <filename>
```

I like nerolinux...

---

### Post by 3Miro on 2009-04-01
> **LawC said:**
> 
"tar xzvf nerolinux-3.5.1.0.tgz -C /"


Did you extract that into "/"? I not the best with such commands, but it looks like it. You probably had a "sudo" before that.

You can do the following:
```

tar xzvf nerolinux-3.5.1.0.tgz -C / >/home/YourUserName/Documents/NeroSUX.txt

```

You will effectively reinstall nero that way, however, in the Docuents folder, you should have a file now that is called NeroSUX.txt. I that file you will see a list of all the files that were extracted and unless some other additional scripts put more files and/or messed some settings, you should be able to just remove (or definitely better) trash them.

---

### Post by rattking on 2009-04-01
> **theozzlives said:**
> ```
sudo apt-get install alien
```
```
sudo alien <filename>
```


next step with this method would be
to install the deb package that alien made in the last command

```
sudo dpkg -i <filename.deb>

```
and just overwrite the first install
then to remove it all

```
sudo apt-get remove --purge <packagename>
``` probably nerolinux

---

### Post by LawC on 2009-04-01
Worked Great, rattking! Thanks alot. I personaly have nothing against nero. My wife wanted me to look for something she could use to make fancier menus than she is doing on devede. Nero didn't fit the bill, and so the search continues... 

Any suggestions? - tovid/todisc gui seemed good, but there's no previews so she didn't wanna spend the time messing with it. K3b Didn't do it for her either.
She want's to try dvdauthor, but it's only available as a .RPM.

Anyway thankyou to everyone for all the help!

---

