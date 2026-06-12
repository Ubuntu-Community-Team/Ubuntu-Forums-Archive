---
title: "How do I install bluej [ JAVA ]"
date: 2006-01-20
forum: Desktop Environments
---

### Post by ade234uk on 2006-01-20
The course I am starting requires me to use bluej which helps you learn JAVA. 

They would like us to use Windows but they do have a linux version. How do I install / run the Linux version?

Visit [http://www.bluej.org/](http://www.bluej.org/) for more information.

Last thing I want to do os go back and run Windows grrrrrrrrrr

---

### Post by DaMasta on 2006-01-20
You have java installed? If so, straight from the site: [http://www.bluej.org/download/install.html](http://www.bluej.org/download/install.html)

---

### Post by Benzino on 2007-07-30
I'm gonna bump this instead of making a new thread.

When I try running the install command from Terminal, I get this:
>         
Failed to load Main-Class manifest attribute from bluej-220.jar


Any ideas?  I also need this for a class and am NOT going back to Windows just for this class.
Thanks!

---

### Post by nthpro on 2007-09-21
Run this

```
sudo apt-get install j2sdk1.4

```

---

### Post by Jukums on 2007-10-16
> **nthpro said:**
> Run this

```
sudo apt-get install j2sdk1.4

```

hey thanks!!! worked and i installed blueJ...

though I have another problem now... it comes up with error message that can't create VM and there's only thing in faq on the blueJ about windows - says that firewall probably is blocking tcp/ip which is needed for VM

My guess is that it's smth to do with the fact that by default all ports and everything is closed on ubuntu? is that correct? 

I'm running Gutsy on amd64

---

### Post by Jukums on 2007-10-18
ne1?

---

### Post by Grignak on 2007-10-20
>though I have another problem now... it comes up with error message that can't create 
>VM and there's only thing in faq on the blueJ about windows - says that firewall probably is
> blocking tcp/ip which is needed for VM

Please post a copy of the exact error message you're getting, and I'll try to replicate the problem.  

While I wait for your reply, I'll install BlueJ on the new installation of Ubuntu 7.10 in front of me, so the solution (if I can find one) works for the next person too.

---

### Post by Jukums on 2007-10-20
> **Grignak said:**
> >though I have another problem now... it comes up with error message that can't create 
>VM and there's only thing in faq on the blueJ about windows - says that firewall probably is
> blocking tcp/ip which is needed for VM

Please post a copy of the exact error message you're getting, and I'll try to replicate the problem.  

While I wait for your reply, I'll install BlueJ on the new installation of Ubuntu 7.10 in front of me, so the solution (if I can find one) works for the next person too.

I've resolved thing anyway... i think BlueJ uses at least java 5 at least that's what my tutor said that we will use Java 5 which is together with stuff of book OBJECTS FIRST WITH JAVA, book using BlueJ... so I thought I might upgrade JAVA 
When I upgraded (I'm testing it on 6 - no probs so far) everything is running like a charm! Thanks for your response anyway :)

---

### Post by heathbar5477 on 2007-10-24
i'm sure this is an idiotic question, but i'm doing no good just sitting here, so how do i get bluej to run after i did that command line install mentioned above "sudo apt-get install j2sdk1.4"?

---

### Post by Sorivenul on 2007-10-25
> **heathbar5477 said:**
> i'm sure this is an idiotic question, but i'm doing no good just sitting here, so how do i get bluej to run after i did that command line install mentioned above "sudo apt-get install j2sdk1.4"?

From my knowledge, the apt-get you used just installs Java SDK 1.4.  From my limited use of BlueJ I believe it depends on Java 5.0 or higher as discussed above.  Just upgrade your Java version, and run your install of BlueJ.  Should work.

---

### Post by Jukums on 2007-10-26
> **Sorivenul said:**
> From my knowledge, the apt-get you used just installs Java SDK 1.4.  From my limited use of BlueJ I believe it depends on Java 5.0 or higher as discussed above.  Just upgrade your Java version, and run your install of BlueJ.  Should work.

Indeed...
BlueJ "runs" with Java 1.4, It would open BlueJ and then comes up with an error message.

in order to run BlueJ properly you should install java5 or higher on you machine

```
sudo apt-get install sun-java5-jdk
```

tell ubuntu to use sun java 1.5
```
sudo update-java-alternatives -s java-1.5.0-sun
```

change to the directory where bluej.jar file is and
do
```
java -jar bluej.jar
```

or right click directly bluej file and "open with sun 5.0 runtime"

that should do the trick

---

### Post by Jojan on 2007-11-10
I have some more problem. Since I'm a newbie, I have no clue WHERE I should install BlueJ.

---

### Post by Jojan on 2007-11-20
Can't anyone help me?

---

### Post by Jukums on 2007-11-21
download jar file from blueJ website

then open terminal and copy-paste those lines of code provided, if any probs, shout! 

ta.

---

