---
title: "Using Stata on Ubuntu"
date: 2007-05-29
forum: Education &amp; Science
---

### Post by can.lu on 2007-05-29
I haven't found xStata therefore I am using Stata with Wine on Ubuntu. It seems to work fine. But I was wondering whether there could be any potential problems or found problems. I am working on a project and don't want to jeopardize my work.

Thank you.

---

### Post by anoir on 2007-05-29
What do you mean by "I haven't found xStata therefore I am using Stata with Wine on Ubuntu"? Stata has the linux version for the same price.

Running software on wine always have some issues. It is slower especially in graphics related work. And the next version might not work, or wine update may cause problem.

If you are using Stata for serious research, then running it on wine is a bad idea.

---

### Post by fjf on 2007-05-29
Install virtualbox or vmware and run a virtual machine with some of the windozes around.  That will be trouble-free.  I am trying to replace sigmaplot and sigmastat, but it is not easy ;)

---

### Post by lordmorley on 2008-05-07
Stata rocks, but if you have already purchased it for windoze, try using R. R is well-documented, and I cannot think of anything it cannot do. OK, the graphics aren't that great, but neither are the graphics in stata. There's my $0.02.

---

### Post by cpbl on 2008-08-20
Has anyone installed Stata 10 on Ubuntu 8.04 and had xstata run smoothly?

The dynamically linked version did not work due to a libtiff missing package, but the statically linked one launches alright.

But the fonts are just awful. The GUI results display is impossibly slow and the fonts do not line up (are mistakenly proportional?) and text is overwritten on other text in the help window.

Stata claims this is not common.  Really??

Have you had this problem? I think I've a pretty plain installation of Ubuntu 8.04 on an intel laptop, except that it's 64bit.

---

### Post by cpbl on 2008-08-21
Solutions to these various problems turned out to be:
change font preferences to Courier 10pitch at 10pt. Then the xstata is fast and readable.

Make sure ~/.stata10 is not owned by root (mistake from installation process? Come on, Stata! You can do better), since having it so makes remembering preferences impossible.

---

### Post by stanton816 on 2008-11-10
Okay.  I just looked at the Stata site and it didn't list Ubuntu as an OS that can run Stata.  So, does this mean that if I buy the linux version of Stata I will have problems?

---

### Post by PGScooter on 2008-11-10
stanton, I think that means that you might have to tweak a few things as mentioned in this thread. But my guess is that once you make those small tweaks, you will not have any problems. I am just going to wait for the next version of Stata to come out and then will definitely buy it for Linux. I would be so excited to have Stata for ubuntu!! can't wait..

Would anyone be down to coordinate an emailing of ubuntu users asking for them to start ubuntu? let me know..

---

### Post by chrisby on 2009-01-18
dynamically linked works fine.  It looks for libtiff.so.3, but if you make a symbolic link the program works great.  Here are the instructions for a ubuntu install.  I first did this with hardy, but it works fine with intrepid

I have stata 10 installed on ubuntu and it works perfectly. Here is how I got it to run:

mkdir /usr/local/stata10
cd /usr/local/
chmod a+rx /usr/local/stata10
cd /usr/local/stata10
mkdir /tmp/statainstall
cp -r /media/cdrom0 /tmp/statainstall
/tmp/statainstall/cdrom0/install

follow prompts

now xstata-se doesn't run because it is looking for libtiff.so.3

This is old so make a symbolic link to your current version

ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3

now stata should run fine.


> **cpbl said:**
> Has anyone installed Stata 10 on Ubuntu 8.04 and had xstata run smoothly?

The dynamically linked version did not work due to a libtiff missing package, but the statically linked one launches alright.

But the fonts are just awful. The GUI results display is impossibly slow and the fonts do not line up (are mistakenly proportional?) and text is overwritten on other text in the help window.

Stata claims this is not common.  Really??

Have you had this problem? I think I've a pretty plain installation of Ubuntu 8.04 on an intel laptop, except that it's 64bit.

---

### Post by redseventyseven on 2009-03-24
I can confirm that Stata10 for Unix works fine in Linux Mint Felicia (which is derived from Ubuntu Intrepid).

> Okay. I just looked at the Stata site and it didn't list Ubuntu as an OS that can run Stata. So, does this mean that if I buy the linux version of Stata I will have problems?

I had a quick look at the Stata website too, and I think this page ([http://www.stata.com/products/opsys.html#unix](http://www.stata.com/products/opsys.html#unix)) is the one you saw. It says that Stata for Unix will run on:

> *Any* 32-bit (x86 or compatible), or 64-bit (Intel Itanium, x86-64 or compatible) running Linux
(emphasis mine)

So it runs on any Linux-based system, of which Ubuntu is just one. It doesn't list Ubuntu specifically, because there are so many. For the record, I've seen it working in Ubuntu, Fedora and Mint. For Ubuntu and Mint I encountered the libtiff.3.so problem but the fix that chrisby suggested worked perfectly. No other issues.

Of course, your mileage may vary.

---

### Post by eumetaxas on 2009-03-25
Confirm.
xstata 10 works fine in Ubuntu. 
But i am making my jump to R - moving from stata to R isn't to difficult.

---

### Post by chrisby on 2009-04-24
@eumetaxas

How is R now (genuine question, I am not trolling)?  I played with it a little bit when I started graduate school, but felt like I was reinventing the wheel coding things built into stata.

---

### Post by mdwy62 on 2009-04-29
These directions were fantastic! Thank you. A couple of comments. 

First, I think it's worth point out that we have to be logged on as root to do this. 

Second, there is a typo in the install line. cdrom0 shouldn't be there:
/tmp/statainstall/install

Question - the last time I installed Stata for Linux I think I was able to update Stata (e.g., update all) without starting Stata as root. I don't remember how I got this to work. Does anybody know how to do this?

Thanks again - these instructions really should be available on the Stata website. 


> **chrisby said:**
> dynamically linked works fine.  It looks for libtiff.so.3, but if you make a symbolic link the program works great.  Here are the instructions for a ubuntu install.  I first did this with hardy, but it works fine with intrepid

I have stata 10 installed on ubuntu and it works perfectly. Here is how I got it to run:

mkdir /usr/local/stata10
cd /usr/local/
chmod a+rx /usr/local/stata10
cd /usr/local/stata10
mkdir /tmp/statainstall
cp -r /media/cdrom0 /tmp/statainstall
/tmp/statainstall/cdrom0/install

follow prompts

now xstata-se doesn't run because it is looking for libtiff.so.3

This is old so make a symbolic link to your current version

ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3

now stata should run fine.

---

### Post by cmfrtblynmb on 2009-11-24
Also after doing all these, you may have to run this one as well:

```
sudo ln -s /usr/lib/libgtksourceview-2.0.so.0 /usr/lib/libgtksourceview-1.0.so.0

```

---

### Post by cmfrtblynmb on 2009-11-24
Also, after running all these:

> **chrisby said:**
> dynamically linked works fine.  It looks for libtiff.so.3, but if you make a symbolic link the program works great.  Here are the instructions for a ubuntu install.  I first did this with hardy, but it works fine with intrepid

I have stata 10 installed on ubuntu and it works perfectly. Here is how I got it to run:

mkdir /usr/local/stata10
cd /usr/local/
chmod a+rx /usr/local/stata10
cd /usr/local/stata10
mkdir /tmp/statainstall
cp -r /media/cdrom0 /tmp/statainstall
/tmp/statainstall/cdrom0/install

follow prompts

now xstata-se doesn't run because it is looking for libtiff.so.3

This is old so make a symbolic link to your current version

ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3

now stata should run fine.

you may have to run this last piece of command as well, then you'll be fine:

```
sudo ln -s /usr/lib/libgtksourceview-2.0.so.0 /usr/lib/libgtksourceview-1.0.so.0
```

---

### Post by den2042 on 2010-05-13
Thank you so much! Helped a lot!

---

### Post by Benic on 2010-07-15
Did you guys manage to install Stata in 10.04? I've recently done a clean install of Lucid, but I just can't install Stata. Whenever I come to the last command, the install command, I get "command not found", with or without ./

I just don't get it, do I miss a prerequisite?

---

### Post by beew on 2010-08-03
Hi, 

Just found this thread when searching. I have just installed STATA 10 on my Ubuntu 10.04 laptop. It is working fine, except when I try to update. I got the error message the "servers refused to send files". I looked up the stata site and apparently it has something to do with proxy settings, but I have not set any proxy as far as I know and the trouble shooting tips at STATA's site makes sense only for Windows (click menu bar and choose preference... there is no bloody menu bar in the Linux version!)

I wonder if anyone knows what the problem is and how to work around it. Thanks.

---

### Post by beew on 2010-08-03
Oh, nevermind. It turns out to be just bad connection. It has updated successfully. :)

---

### Post by knattlhuber on 2010-11-02
Speaking of updating: There is a *really bad* bug in Stata 11 when running under Ubuntu 10.04. It can seriously compromise the accuracy of your calculations (e.g. it changed the values of a variable when I renamed it)
There is an update that fixes the bug, so I would urgently recommend to run
```
update all
```
in Stata.
It's probably also a good idea to re-run your calculations from the last couple of months, especially if some results didn't seem to make sense...

---

### Post by fbotero on 2011-03-05
I'm having a problem with the 'update all' command. Stata claims that "cannot write in directory /usr/local/stata11/ado/updates/".

I cant't get Stata to run as super user. Tried the following:

sudo stata
sudo: stata: command not found

sudo xstata
sudo: xstata: command not found

How do I run Stata with privileges so that it can update itself?

---

### Post by knattlhuber on 2011-03-05
Seems like */usr/local* is not in your PATH variable.

Try the complete path, e.g.
```
sudo /usr/local/stata11/xstata
```

If you have Stata/SE, do
```
sudo /usr/local/stata11/xstata-se
```

---

### Post by MetapostAddict on 2011-04-15
I seem to be having trouble with Stata in Ubuntu 11.04.  It was working fine before I updated.  

After updating, I got the error message "error while loading shared libraries: libtiff.so.3: cannot open shared object file: No such file or directory."  I created a link from libtiff.so.4 and named it libtiff.so.3 and I got the same message.  The libtiff.so.4 was actually in my /usr/lib32, so I copied the link to /usr/lib.  

I then got the following error message: "xstata: error while loading shared libraries: libtiff.so.3: wrong ELF class: ELFCLASS32"  

The file is 32 bit: I typed "file /usr/lib/libtiff.so.4.3.3" and got "/usr/lib32/libtiff.so.4.3.3: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped"  I'm running the 64 bit version of Stata.

Any ideas on how to fix this?

---

### Post by knattlhuber on 2011-04-15
I'm not running 11.04 so I can't reproduce the error and I just have to guess:

1) Is there a 64-bit version of libtiff that you could try?
2) You could try installing the statically linked Stata version. That should (theoretically) install all required libraries.

---

### Post by MetapostAddict on 2011-04-15
I don't think there's a 64 bit libtiff.  I'll looking into installing the statically linked version.  It's puzzling to me that it worked before and won't worked now... I don't see what's relevant that's changed.

---

### Post by knattlhuber on 2011-04-15
Well, I guess the update installed a new version of libtiff that doesn't work with Stata. Installing the statically linked version will install all libraries that Stata needs instead of linking to what's already there (and doesn't work in your case).
Please let us know how it went.

---

### Post by MetapostAddict on 2011-04-16
well thanks for your help.  I'm pretty busy now, so for the time being I'm going to use stata instead of xstata, and I'll hope things resolve themselves.

---

### Post by knattlhuber on 2011-04-29
> **MetapostAddict said:**
> I seem to be having trouble with Stata in Ubuntu 11.04.  It was working fine before I updated.  

After updating, I got the error message "error while loading shared libraries: libtiff.so.3: cannot open shared object file: No such file or directory."  I created a link from libtiff.so.4 and named it libtiff.so.3 and I got the same message.  The libtiff.so.4 was actually in my /usr/lib32, so I copied the link to /usr/lib.  

I then got the following error message: "xstata: error while loading shared libraries: libtiff.so.3: wrong ELF class: ELFCLASS32"  

The file is 32 bit: I typed "file /usr/lib/libtiff.so.4.3.3" and got "/usr/lib32/libtiff.so.4.3.3: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped"  I'm running the 64 bit version of Stata.

Any ideas on how to fix this?

Upgraded to Natty and encountered the same problem.

```
sudo ln -s /usr/lib/i386-linux-gnu/libtiff.so.4.3.3 /usr/lib/libtiff.so.3
```

fixed it for me.

---

### Post by MetapostAddict on 2011-05-01
> **knattlhuber said:**
> Upgraded to Natty and encountered the same problem.

```
sudo ln -s /usr/lib/i386-linux-gnu/libtiff.so.4.3.3 /usr/lib/libtiff.so.3
```

fixed it for me.

And you're using the 64bit version of Stata?  

This did not work for me.  It's what I tried before, and I still get "xstata: error while loading shared libraries: libtiff.so.3: wrong ELF class: ELFCLASS32"

---

### Post by MetapostAddict on 2011-05-01
As an aside, it seems strange that you even have a folder at "/usr/lib/i386-linux-gnu/".  I assumed all natty users had the same file structure for root.  I have /usr/lib32/, which contains the libtiff.so.4.3.3.

---

### Post by knattlhuber on 2011-05-01
I'm on 32-bit Natty. Sorry, should've mentioned that. I just wanted to put the syntax out there for the other 32-bit Ubuntu/Stata users.

Apart from the statically linked Stata version, you could
...try an older 64-bit version of libtiff ([http://packages.ubuntu.com/maverick-updates/libtiff4](http://packages.ubuntu.com/maverick-updates/libtiff4) or [http://packages.ubuntu.com/natty/libtiff4](http://packages.ubuntu.com/natty/libtiff4))
...try to install dependencies using getlibs ([http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790) or [http://explore-ubuntu.blogspot.com/2010/04/getlibs.html](http://explore-ubuntu.blogspot.com/2010/04/getlibs.html))
...compile libtiff from source

Yes, the i386 subfolder is odd but I have that on both of my machines.

---

### Post by knattlhuber on 2011-05-01
I just installed 64-bit in Virtualbox and then installed the 64-bit version of Stata (dynamically linked).

I got "the usual error messages" ([http://linuxscrapbook.wordpress.com/2010/01/24/run-stata-11-with-gui-under-ubuntu-9-10/](http://linuxscrapbook.wordpress.com/2010/01/24/run-stata-11-with-gui-under-ubuntu-9-10/)) but after

```
sudo ln -s /usr/lib/x86_64-linux-gnu/libtiff.so.4.3.3 /usr/lib/libtiff.so.3
sudo ln -s /usr/lib/libgtksourceview-2.0.so.0 /usr/lib/libgtksourceview-1.0.so.0
sudo apt-get install libgtksourceview1.0-0
```

Stata worked without problems.

As you posted your questions before the official Natty release and since your /usr/lib folder look different than mine, maybe your problems have to do with the fact that you used the beta version?!

---

### Post by celian on 2011-05-02
I was running a 64-bit 10.10, and 64-bit Stata 11c, and when I upgraded, I got the libtiff error, with the whole ELF deal as well.

This single command fixed the problem for me, providing a 64-bit libtiff.so.3 (dynamic link to the libtiff.so.4).


sudo ln -s /usr/lib/x86_64-linux-gnu/libtiff.so.4.3.3 /usr/lib/libtiff.so.3

---

### Post by MetapostAddict on 2011-06-24
Yeah, I'm going to chalk this one up to my using the beta version of Natty.  All's well now.  I didn't have to bother with libgtksourceview1.

Thanks for the help.

---

### Post by ftballman125 on 2011-07-26
I'm trying to install Stata10 on 64-bit Ubuntu 11.04 and running into troubles. I tried using the same basic code I've had work on the 32-bit version, and it's not working well. The install and serial number verification go fine, and I have tried the various libtiff reassignments listed above, but nonetheless when I type "xstata" or "xstata-se" I get the reply "command not found".

Any help or a brief walk-through of what you guys have done to get it to work on 64-bit would be greatly appreciated.

Thanks.

---

### Post by knattlhuber on 2011-07-26
Have you tried this: [http://ubuntuforums.org/showpost.php?p=10525413&postcount=22](http://ubuntuforums.org/showpost.php?p=10525413&postcount=22)

---

### Post by ftballman125 on 2011-07-26
when you refer to "PATH variable" what exactly are you referring to? I have tried executing the command via that path, if that's what you're asking, yes.

Thanks for the help.

---

### Post by knattlhuber on 2011-07-26
Never mind the PATH variable for now. Let's first find out in which location it is installed.

Type

```
locate xstata
```

in a terminal window. I expect that it's in /usr/local/stata (NOT /usr/local/stata11 as in my other post).

In that case

```
/usr/local/stata/xstata
```

should start Stata (or whatever path the locate command showed).

If that works, you can add that path permanently to your PATH variable to save you from always typing the full path:

```
cd
echo 'export PATH=$PATH:/usr/local/stata' >> .bashrc

```
Note that for the export command you use only the path to the folder, not the complete path. Restart the terminal and type

```
xstata
```

to test.

---

### Post by ftballman125 on 2011-07-26
I appreciate the help. It's installed in the correct directory and I have properly cross-checked the references. "/usr/local/stata10/" and when I try to run xstata from that directory, it reports that the command cannot be found, though the files are clearly installed in the directory...

---

### Post by knattlhuber on 2011-07-27
Strange. Not sure what's going on.

- Did you do *xstata* or *./xstata* when in */usr/local/stata10* ? Only the latter will work.
- Did you run *./stinit* at the end of the installation?
- Is xstata executable (although I believe that shouldn't give a "command not found" error) ? -- (Fix: sudo chmod +x /usr/local/stata10/xstata)

That's all I can think of..

---

### Post by slamhound on 2011-07-28
> **ftballman125 said:**
> I'm trying to install Stata10 on 64-bit Ubuntu 11.04 and running into troubles. I tried using the same basic code I've had work on the 32-bit version, and it's not working well. The install and serial number verification go fine, and I have tried the various libtiff reassignments listed above, but nonetheless when I type "xstata" or "xstata-se" I get the reply "command not found".

Any help or a brief walk-through of what you guys have done to get it to work on 64-bit would be greatly appreciated.

Thanks.


Are you still using the 32-bit version of Stata on your 64-bit system?  When I've tried to run 32-bit programs on 64-bit, these are the symptoms I get (says file not found even though it's there). You can look here for ways to get this to work if that is the problem: [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by mdwy62 on 2011-08-14
Thanks - just upgraded to 11.04. find libtiff.so did not return this one from the subfolder. Linked as you suggested and xstata is back up and running.

---

### Post by cmfrtblynmb on 2011-09-24
I just installed 11.10, 64 bit version.

I have created all of the proper links:

```
sudo ln -s /usr/lib/x86_64-linux-gnu/libtiff.so.4.3.3 /usr/lib/libtiff.so.3
sudo ln -s /usr/lib/libgtksourceview-2.0.so.0 /usr/lib/libgtksourceview-1.0.so.0
```



but now I get this when I run xstata:

"GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported"

---

### Post by ctijacob on 2011-10-09
> **cmfrtblynmb said:**
> 
but now I get this when I run xstata:

"GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported"

I have performed the same steps and get the same.. I have it working fine in 11.04 but can't get it working in 11.10.

---

### Post by AntoineT on 2011-10-14
> **ctijacob said:**
> I have performed the same steps and get the same.. I have it working fine in 11.04 but can't get it working in 11.10.

Hi,

Have you managed to get it working?

I am also using 11.10 64 bits. I had it almost working, but linking to the new libraries in Oneiric:

/usr/lib/x86_64-linux-gnu/libtiff.so.4.3.4
instead of
/usr/lib/x86_64-linux-gnu/libtiff.so.4.3.3

and to 
/usr/lib/libgtksourceview-3.0.so.0
instead of 
/usr/lib/libgtksourceview-2.0.so.0

It seems to work, but Stata crashes when I open the do file editor.

In 11.04 this was solved by installing libgtksourceview1.0-0
however, it is not available from the Oneiric repos...

I have a machine on which I have upgraded from 11.04 to 11.10, and everything works fine. libgtksourceview1.0-0 is still present, so I guess this is the culprit...

---

### Post by AntoineT on 2011-10-14
> **AntoineT said:**
> Hi,

Have you managed to get it working?

I am also using 11.10 64 bits. I had it almost working, but linking to the new libraries in Oneiric:

/usr/lib/x86_64-linux-gnu/libtiff.so.4.3.4
instead of
/usr/lib/x86_64-linux-gnu/libtiff.so.4.3.3

and to 
/usr/lib/libgtksourceview-3.0.so.0
instead of 
/usr/lib/libgtksourceview-2.0.so.0

It seems to work, but Stata crashes when I open the do file editor.

In 11.04 this was solved by installing libgtksourceview1.0-0
however, it is not available from the Oneiric repos...

I have a machine on which I have upgraded from 11.04 to 11.10, and everything works fine. libgtksourceview1.0-0 is still present, so I guess this is the culprit...


Okay, so in fact what I did (Oneiric 64 bits, Stata 11 64 bits) was:
sudo ln -s /usr/lib/x86_64-linux-gnu/libtiff.so.4.3.4 /usr/lib/libtiff.so.3

sudo apt-get install libgtksourceview2.0-0

sudo ln -s /usr/lib/libgtksourceview-2.0.so.0 /usr/lib/libgtksourceview-1.0.so.0

sudo apt-get install libgnomeprint2.0-0


This is ok to get the GUI launched, but opening the do-file editor still crashes Stata...

---

### Post by ctijacob on 2011-10-15
> **AntoineT said:**
> Okay, so in fact what I did (Oneiric 64 bits, Stata 11 64 bits) was:
sudo ln -s /usr/lib/x86_64-linux-gnu/libtiff.so.4.3.4 /usr/lib/libtiff.so.3

sudo apt-get install libgtksourceview2.0-0

sudo ln -s /usr/lib/libgtksourceview-2.0.so.0 /usr/lib/libgtksourceview-1.0.so.0

sudo apt-get install libgnomeprint2.0-0


This is ok to get the GUI launched, but opening the do-file editor still crashes Stata...

OK, looking back at what I had quoted I suppose I should have examined it a little closer, I had linked libgtksourceview-1.0.so.0 to libgtksourceview-3.0.so.0.0.0, I suppose that this is why I was getting the error.. I had installed libgtksourceview2.0-0, removed my other link and recreated it pointing to the newly installed library and the GUI launches.

I'm able to open up data sets fine, I'm not doing any intense analysis as I'm a Soc major and we're not required to do much with our data but I created a blank .do file and it opened it w/o crashing.. let me know if there are any troubleshooting steps that you want me to perform to try to narrow down any issues. I currently have 11.04 and 11.10 so I can run in both and see if I get any different results as well.

Also, are you launching the program from terminal or a shortcut? If you're using something the shortcut in the app drawer, try launching it from terminal and see if any errors occur when it crashes.

---

### Post by ctijacob on 2011-10-15
> **AntoineT said:**
> Okay, so in fact what I did (Oneiric 64 bits, Stata 11 64 bits) was:
sudo ln -s /usr/lib/x86_64-linux-gnu/libtiff.so.4.3.4 /usr/lib/libtiff.so.3

sudo apt-get install libgtksourceview2.0-0

sudo ln -s /usr/lib/libgtksourceview-2.0.so.0 /usr/lib/libgtksourceview-1.0.so.0

sudo apt-get install libgnomeprint2.0-0


This is ok to get the GUI launched, but opening the do-file editor still crashes Stata...

OK, so I investigated this and I was having the same issue, here's how I resolved it..

While in Ubuntu 11.10, I opened the do file editor and it crashes with error:
 undefined symbol: gtk_source_buffer_set_check_brackets
(viewed from terminal)

So, I rebooted in 11.04 to see if I had the same error there, sure enough, I just hadn't used to do file editor to even realize it. So, in 11.04:

'sudo apt-get install libgtksourceview1.0-0'

and this solved my issue.

Back to Ubuntu 11.10:
I went into my other partition (11.04) and grabbed the libgtksourceview-1.0.so.0.0.0 and copied it to /usr/lib and launched STATA, still had the same issue, so I deleted the file (don't want to leave stuff there and it cause problems later)

I saw that you had done 'sudo apt-get install libgnomeprint2.0-0' and I had not, so I tried that to no avail:
E: Couldn't find any package by regex 'libgnomeprint2.0-0'

I had copied the other packages installed when I installed libgtksourceview1.0-0 to a text file, so I investigated that and found: libgnomeprint2.2-0, so 'sudo apt-get install libgnomeprint2.2-0' and it was successful.

But now while launching stata I get:
./xstata: error while loading shared libraries: libgtksourceview-1.0.so.0: cannot open shared object file: No such file or directory

I saw that it was whining about libgtksourceview-1.0.so.0 (even though I have a symbolic link pointing elsewhere) so I copied
libgtksourceview-1.0.so.0.0.0 from my 11.04 partition back into my /usr/lib directory and that seems to have resolved the issue.

I understand that this isn't an ideal workaround since you can just install libgtksourceview1.0-0 from the repos, but if you can get it elsewhere it may fix your issue.

If anyone else is having similar issues and needs a more in-depth how-to, just ask.. AntoineT just seems to know how to perform the aforementioned steps w/o greater detail.

---

### Post by AntoineT on 2011-10-15
> **ctijacob said:**
> OK, so I investigated this and I was having the same issue, here's how I resolved it..

While in Ubuntu 11.10, I opened the do file editor and it crashes with error:
 undefined symbol: gtk_source_buffer_set_check_brackets
(viewed from terminal)

Same here

> **ctijacob said:**
> So, I rebooted in 11.04 to see if I had the same error there, sure enough, I just hadn't used to do file editor to even realize it. So, in 11.04:

'sudo apt-get install libgtksourceview1.0-0'

and this solved my issue.



That's also how I did in 11.04

> **ctijacob said:**
> Back to Ubuntu 11.10:
I went into my other partition (11.04) and grabbed the libgtksourceview-1.0.so.0.0.0 and copied it to /usr/lib and launched STATA, still had the same issue, so I deleted the file (don't want to leave stuff there and it cause problems later)

I saw that you had done 'sudo apt-get install libgnomeprint2.0-0' and I had not, so I tried that to no avail:
E: Couldn't find any package by regex 'libgnomeprint2.0-0'

I had copied the other packages installed when I installed libgtksourceview1.0-0 to a text file, so I investigated that and found: libgnomeprint2.2-0, so 'sudo apt-get install libgnomeprint2.2-0' and it was successful.


Indeed, libgnomeprint2.2-0 is in the dependencies of libgtksourceview1.0-0. But I'm not sure I understood, you were first unable to install it from the Oneiric repos?

> **ctijacob said:**
> But now while launching stata I get:
./xstata: error while loading shared libraries: libgtksourceview-1.0.so.0: cannot open shared object file: No such file or directory

I saw that it was whining about libgtksourceview-1.0.so.0 (even though I have a symbolic link pointing elsewhere) so I copied
libgtksourceview-1.0.so.0.0.0 from my 11.04 partition back into my /usr/lib directory and that seems to have resolved the issue.

So, am I correct in saying that copying libgtksourceview-1.0.so.0.0.0 and libgtksourceview-1.0.so.0 to your Oneiric partition only worked after you installed libgnomeprint2.2-0 from the repos, but not before?

One last question, you are using the 64 bit versions, right? I was using 32 bits before, and I was given the link to this Statalist message [http://www.stata.com/statalist/archive/2011-04/msg01297.html](http://www.stata.com/statalist/archive/2011-04/msg01297.html) that seems to indicate that having Stata run in the 64 bits version was a tad harder than in 32 bits.

Antoine

---

### Post by ctijacob on 2011-10-15
> **AntoineT said:**
> 
Indeed, libgnomeprint2.2-0 is in the dependencies of libgtksourceview1.0-0. But I'm not sure I understood, you were first unable to install it from the Oneiric repos?

I was unable to find libgnomeprint2.0-0 that you had mentioned, but noticed that libgnomeprint2.2-0 was installed when I installed libgtksourceview1.0-0 in 11.04, so I installed libgnomeprint2.2-0.

> **AntoineT said:**
> 
So, am I correct in saying that copying libgtksourceview-1.0.so.0.0.0 and libgtksourceview-1.0.so.0 to your Oneiric partition only worked after you installed libgnomeprint2.2-0 from the repos, but not before?

libgtksourceview-1.0.so.0.0.0 I copied over from 11.04, libgtksourceview-1.0.so.0 I did not copy, it was a link that I *DID* have linked to libgtksourceview-2.0.so.0 just as you had in your earlier post, but when I just checked the link, it seems to have been redirected:

jacob@happylappy:/usr/lib$ ls -l | grep libgtksourceview-1.0.so.0
lrwxrwxrwx  1 root root           29 2011-10-15 04:51 libgtksourceview-1.0.so.0 -> libgtksourceview-1.0.so.0.0.0

I would suspect that this should be done automatically sometime after downloading libgnomeprint2.2-0 and then copying libgtksourceview-1.0.so.0.0.0 into your library (since it was for me) but if you have problems you may want to check it to make sure.

And yes, this only worked after installing libgnomeprint2.2-0. When I tried to just copy the file over nothing happened.

> **AntoineT said:**
> 
One last question, you are using the 64 bit versions, right? I was using 32 bits before, and I was given the link to this Statalist message [http://www.stata.com/statalist/archive/2011-04/msg01297.html](http://www.stata.com/statalist/archive/2011-04/msg01297.html) that seems to indicate that having Stata run in the 64 bits version was a tad harder than in 32 bits.

Yes, I am running the 64-bit versions.

I think that you're very close to having it running, pretty sure all you need to do is:

-sudo apt-get install libgnomeprint2.2-0
-Copy libgtksourceview-1.0.so.0.0.0 into /usr/lib
-Verify the link to libgtksourceview-1.0.so.0 points to your newly created libgtksourceview-1.0.so.0.0.0

It sounds like you do have 11.04 installed somewhere, but if you don't and can't find libgtksourceview-1.0.so.0.0.0 anywhere, I can email it to you if you give me your info.

---

### Post by AntoineT on 2011-10-15
Thanks ctijacob.

I have 11.04 on my laptop, and did a fresh install of Oneiric on my work computer. I'll email the files to myself and try your solution next week. I'll keep you posted.

---

### Post by AntoineT on 2011-10-17
Ok, I managed to get it working (yay!, thanks ctijacob)

Instead of copying files to /usr/lib (which did not work because I had the 32 bits version), I went to [http://packages.ubuntu.com/natty/amd64/libs/libgtksourceview1.0-0](http://packages.ubuntu.com/natty/amd64/libs/libgtksourceview1.0-0)
and clicked on libgtksourceview-common (<< 1.9) because this dependency could not be satisfied when installing libgtksourceview-1.0. I downloaded the .deb and installed it through the software center.
I then went back to [http://packages.ubuntu.com/natty/amd64/libs/libgtksourceview1.0-0](http://packages.ubuntu.com/natty/amd64/libs/libgtksourceview1.0-0) and downloaded the .deb for the 64bits architecture, and installed it through the software center.

Everything now works fine, and the GUI does not crash anymore upon opening the do file editor.

---

### Post by adam.smith on 2011-11-03
thanks everyone, just upgraded from 11.04, this saved me tons of time - I did everything as above, except I didn't install the .deb, but downloaded it, unpacked it and copyed
libgtksourceview-1.0.so.0.0.0 to usr/lib, created the symlink, et voila, all's working.

---

### Post by tramir on 2012-11-27
> **cmfrtblynmb said:**
> I just installed 11.10, 64 bit version.

I have created all of the proper links:

```
sudo ln -s /usr/lib/x86_64-linux-gnu/libtiff.so.4.3.3 /usr/lib/libtiff.so.3
sudo ln -s /usr/lib/libgtksourceview-2.0.so.0 /usr/lib/libgtksourceview-1.0.so.0
```



but now I get this when I run xstata:

"GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported"
If you have the error:

>  GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported"

What worked for me was to install the Natty  version of libgtksourceview1.0 and libgtksourceview-common (from ubuntu-updates, they're not available on packages.ubuntu.com anymore). After that, Stata seems to be running ok.

---

### Post by Hyvver on 2012-12-15
Yep, similar command.  The instructions are for both USB and SD.  I just use USB as the examples because that's what I was using.  So, anything for USB you should also do for SD I'll make any notes of when you do something different.

---

