---
title: "HjSplit Alternative?"
date: 2009-03-29
forum: General Help
---

### Post by nukem170 on 2009-03-29
Does anyone use an alternative to HjSplit? I think there's a linux alternative on the official website but I couldnt get it to work with Ubuntu. If anyone uses any other program can you please tell me the steps that you took to install it?

---

### Post by FluffyElmo on 2009-03-29
lxsplit: [http://lxsplit.sourceforge.net/](http://lxsplit.sourceforge.net/)

I installed the deb without any issues, just download and click it. It also appears to be in the repositories, you may have to enable all the repositories, just search Synaptic for lxsplit and see if it shows up. 

If you run into specific problems post here and I can try to give more detailed instructions.

---

### Post by zefiriss01 on 2009-05-21
i can't find it on synaptic.

---

### Post by zefiriss01 on 2009-05-21
installed .deb file, and it works great, thanks.

---

### Post by binbash on 2009-05-21
lxsplit or cat command

---

### Post by cb951303 on 2009-05-21
> **nukem170 said:**
> Does anyone use an alternative to HjSplit? I think there's a linux alternative on the official website but I couldnt get it to work with Ubuntu. If anyone uses any other program can you please tell me the steps that you took to install it?

get the java one, it works and has a gui

---

### Post by ricardisimo on 2009-07-03
Where is the java version? I found a rather odd KDE-related, bash-script-looking version on Softpedia, but I have no clue how to work with it.

---

### Post by michy99 on 2009-07-03
You can split files with the split command and put them back together with the cat command. For more information:```
man split
man cat
```

---

### Post by Jazmac on 2009-08-24
No love for 64 bit users.  As much as I love Ubuntu, and I'm a still a linux toddler, finding 64bit support would push me back into Windows.  This is the most frustrating issue I have with Linux.  I need a 64 bit file joiner and man, I can't find it anywhere.

-JazMac

---

### Post by tubasoldier on 2009-08-24
```
cat file1 file2 file3 file4 ect.. > outputfile.extension
```

---

### Post by Jazmac on 2009-08-24
> **tubasoldier said:**
> ```
cat file1 file2 file3 file4 ect.. > outputfile.extension
```

That works for split rar files?

-Jazmac

---

### Post by tubasoldier on 2009-08-24
> **Jazmac said:**
> That works for split rar files?

-Jazmac

no, but file roller will automatically extract the contents out of split rar files without the need for combining them.

---

### Post by Jazmac on 2009-08-24
> **annawei said:**
> Just install deb file,it will work smoothly.

Is there a 64bit deb?

-Jazmac

---

### Post by Jazmac on 2009-08-25
Hello??

-Jazmac

---

### Post by Francewhoa on 2009-09-06
HJsplit for Ubuntu

**STEPS:**
1. Go to [http://www.freebyte.com/hjsplit/#java](http://www.freebyte.com/hjsplit/#java)
3. Download the file 'hjsplit_g.jar (137 Kb)'. 
4. On your desktop. Right click on the file hjsplit_g.jar. 
5. Select 'Open with Sun Java x Runtime'. 
6. Follow instructions on screen. It's a graphical interface. Easy to use.
[IMG]http://www.freebyte.com/img34/hjsplit/hjsplitjava_g1.gif[/IMG]

If not working make sure you have Java install.

---

### Post by fooman on 2009-09-06
> **Onopoc said:**
> HJsplit for Ubuntu

**STEPS:**
1. Go to [http://www.freebyte.com/hjsplit/#java](http://www.freebyte.com/hjsplit/#java)
3. Download the file 'hjsplit_g.jar (137 Kb)'. 
4. On your desktop. Right click on the file hjsplit_g.jar. 
5. Select 'Open with Sun Java x Runtime'. 
6. Follow instructions on screen. It's a graphical interface. Easy to use.
[IMG]http://www.freebyte.com/img34/hjsplit/hjsplitjava_g1.gif[/IMG]

If not working make sure you have Java install.

nice!  ...i *had* been using wine to run hj-split.

thanx.

---

### Post by etheta on 2009-09-19
> **Onopoc said:**
> HJsplit for Ubuntu

**STEPS:**
1. Go to [http://www.freebyte.com/hjsplit/#java](http://www.freebyte.com/hjsplit/#java)
3. Download the file 'hjsplit_g.jar (137 Kb)'. 
4. On your desktop. Right click on the file hjsplit_g.jar. 
5. Select 'Open with Sun Java x Runtime'. 
6. Follow instructions on screen. It's a graphical interface. Easy to use.
[IMG]http://www.freebyte.com/img34/hjsplit/hjsplitjava_g1.gif[/IMG]

If not working make sure you have Java install.


Thanks for the excellent tip. I'd been using terminal cmd's to extract and run each time...

---

### Post by SlappyPappy on 2009-10-05
> **Onopoc said:**
> HJsplit for Ubuntu

**STEPS:**
1. Go to [http://www.freebyte.com/hjsplit/#java](http://www.freebyte.com/hjsplit/#java)
3. Download the file 'hjsplit_g.jar (137 Kb)'. 
4. On your desktop. Right click on the file hjsplit_g.jar. 
5. Select 'Open with Sun Java x Runtime'. 
6. Follow instructions on screen. It's a graphical interface. Easy to use.
[IMG]http://www.freebyte.com/img34/hjsplit/hjsplitjava_g1.gif[/IMG]

If not working make sure you have Java install.

Dude that's sick. Thanks for posting this. Works a treat.

Rock on with your bad HJSplit self. :guitar:

---

### Post by vinan on 2010-01-04
Nice and simpel 

Cheers:) 

> **Onopoc said:**
> HJsplit for Ubuntu

**STEPS:**
1. Go to [http://www.freebyte.com/hjsplit/#java](http://www.freebyte.com/hjsplit/#java)
3. Download the file 'hjsplit_g.jar (137 Kb)'. 
4. On your desktop. Right click on the file hjsplit_g.jar. 
5. Select 'Open with Sun Java x Runtime'. 
6. Follow instructions on screen. It's a graphical interface. Easy to use.
[IMG]http://www.freebyte.com/img34/hjsplit/hjsplitjava_g1.gif[/IMG]

If not working make sure you have Java install.

---

### Post by rreese6 on 2010-02-01
I made a "link to application" desktop link.

In the properties I added under tab "application" at the "Command" line
/usr/lib/jvm/java-6-sun-1.6.0.17/jre/bin/java -jar /usr/share/java/hjsplit_g.jar       

where "/usr/lib/jvm/java-6-sun-1.6.0.17/jre/bin/java" is my sun Java runtime is located
and "/usr/share/java/hjsplit_g.jar"
I copied hjsplit_g.jar to  /usr/share/java/

Now I have a desktop icon to start it.

Check your path to the Sun Runtime and modify the above as necessary.

I am running Kubuntu 8.04LTS

---

### Post by whitey_1 on 2010-03-20
> **Onopoc said:**
> HJsplit for Ubuntu

**STEPS:**
1. Go to [http://www.freebyte.com/hjsplit/#java](http://www.freebyte.com/hjsplit/#java)
3. Download the file 'hjsplit_g.jar (137 Kb)'. 
4. On your desktop. Right click on the file hjsplit_g.jar. 
5. Select 'Open with Sun Java x Runtime'. 
6. Follow instructions on screen. It's a graphical interface. Easy to use.
[IMG]http://www.freebyte.com/img34/hjsplit/hjsplitjava_g1.gif[/IMG]

If not working make sure you have Java install.

I got to step 5 , but when i right click the file there is no option on that menu for 'Open with Sun Java x Runtime'. Do i need to download this sun java x runtime? because i cant find that.

Im a beginner at this thing, can someone help me with this?

---

### Post by fooman on 2010-03-20
> **whitey_1 said:**
> I got to step 5 , but when i right click the file there is no option on that menu for 'Open with Sun Java x Runtime'. Do i need to download this sun java x runtime? because i cant find that.

Im a beginner at this thing, can someone help me with this?

open synaptic (system > administration > synaptic package manager) an
d search for "sun"

when the results of the search are done....find and install "sun-java6-jre".  it will also install a few other dependencies along with it.

hope that helps.

---

### Post by whitey_1 on 2010-03-20
> **fooman said:**
> open synaptic (system > administration > synaptic package manager) an
d search for "sun"

when the results of the search are done....find and install "sun-java6-jre".  it will also install a few other dependencies along with it.

hope that helps.

thanks fooman! sometimes its just that little point in the right direction that needs to solve a problem 

I also got a problem with something else, if you could please take a look, im banging my head on the wall with this other problem
[http://ubuntuforums.org/showthread.php?t=1420973](http://ubuntuforums.org/showthread.php?t=1420973)

Thanks again anyway fooman , great stuff

Gracias!

---

### Post by fooman on 2010-03-20
i see that someone else suggested that you install the ubuntu-restricted-extras ....have you done that?

if not,  then open a terminal (applications > accessories > terminal) and type or copy/paste the following into it:

```
sudo apt-get install ubuntu-restricted-extras
```then press enter...type your password when prompted.

does that help?

also,  what player are you using to play the dvd?  you could always try another player....  "vlc" and "smplayer" are 2 that i prefer.  you can find them in synaptic as well.

---

### Post by spotted zebra on 2010-05-22
> **tubasoldier said:**
> ```
cat file1 file2 file3 file4 ect.. > outputfile.extension
```

can i get some further explanation here. i would like to do it this way since it is native to linux. 

here is what i have tried so far:

```
michael@michael-laptop:~/Downloads$ cat liveandroidv0.3.iso.001 - liveandroidv0.3.iso.002 > liveandroidv0.3.iso.003

```

i hit enter and then it just sits there and does nothing. i tried it with and without the dash between the file names. any help at all would be awesome.

**nevermind i figured it out. it worked as prescribed above i just didn't check the folder for the new file when i was done. **

---

### Post by Vigneshwaran on 2010-09-12
Guys.. I have made a free and better alternative to HJSplit.. It's called JJSplit.. lol

[http://sourceforge.net/projects/jjsplit](http://sourceforge.net/projects/jjsplit)

---

### Post by UncleMonty on 2011-04-18
> **Onopoc said:**
> HJsplit for Ubuntu

**STEPS:**
1. Go to [http://www.freebyte.com/hjsplit/#java](http://www.freebyte.com/hjsplit/#java)
3. Download the file 'hjsplit_g.jar (137 Kb)'. 
4. On your desktop. Right click on the file hjsplit_g.jar. 
5. Select 'Open with Sun Java x Runtime'. 
6. Follow instructions on screen. It's a graphical interface. Easy to use.
[IMG]http://www.freebyte.com/img34/hjsplit/hjsplitjava_g1.gif[/IMG]

If not working make sure you have Java install.


I've installed it but I can't find it under accessories or anything?

---

### Post by lgun on 2011-07-15
[http://www.hjsplit.org/linux/](http://www.hjsplit.org/linux/)

just download unpack and run it, very simple.

---

