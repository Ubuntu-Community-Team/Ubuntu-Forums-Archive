---
title: "How to get video sharing sites java uploaders to work with linux ubuntu lxde"
date: 2011-12-06
forum: Desktop Environments
---

### Post by davegurn on 2011-12-06
Hi Everyone 

You have already helped me without knowing through google and the ubuntu forums search feature and i hope to be able to help in the future after i have read some linux books and got used to the switch from windows to linux! But at the moment i am useless at linux :)

Anyway i have purchased a linux vps due to the massive difference in cost to a windows vps and i intend to use it the help with file and video sharing.

i am trying to use the java uploader located here [COLOR=Blue][Putlocker]("http://www.putlocker.com/")[/COLOR] if you click on "upload files now" the upload window will pop up. And also the one here [COLOR=Blue][veehd]("http://veehd.com/")[/COLOR]

Now my problem is that these are the two main video sites i want to upload to but they seem to have the same type of uploader that does not display a "**[COLOR=red]browse files button[/COLOR]**" on linux but does on windows 7! (so in linux i cant seem to add files to the uploader) Also alot of the other video sites have the same type of uploader and seem to have the same proplem. So if i cannot resolve this i cant upload to the popular video sites and my vps will be unable to do what i purchased it for.

I have uploaded 4 screen shots of the veehd and putlockers uploaders [COLOR=Blue][Here]("http://imageshack.us/g/804/windows7putlockerexampl.png/")[/COLOR]

The first two are on windows 7 seven (where there is a[COLOR=red] browse files button[/COLOR]) and the second two are on ubuntu lxde (where the option to [COLOR=red]browse files[/COLOR] has disappeared.)

So finally lol my question is can i do anything about this or are these sites just purely incompatible with linux?

Heres what ive done on my vps so far

1) Installed lxde -> sudo apt-get install lxde

2) Installed Mozilla Firefox -> sudo apt-get install firefox

3) Installed java -> [COLOR=#4C1130]sudo apt-get install openjdk-6-jre-headless

4) Install Mozilla firefox java icedtea plugin -> sudo apt-get install icedtea6-plugin

and then i checked that icedtea is enabled on firefox.

If anyone is kind enough to offer a solution please could you explain how to do it (ie the sudo code as i am not very good at linux)

Thanks in advance for any help

Oh yeah and i use tightvnc to access the gui and marinara reminded me to mention im running lubuntu natty 32 bit.[/COLOR][COLOR=#4C1130]
[/COLOR]

---

### Post by marinara on 2011-12-06
I'm running Lubuntu Oneric.  I registered on veehd.com.  It works fine.
It also works with putfile.com.
I'm using Lubuntu with PCManFM (by default)

I don't have a fix for you.

---

### Post by davegurn on 2011-12-06
Ok thanks for taking the time to reply! You have actually offered a solution by telling me a confirmed ubunutu version thats working with the sites i want to use. you also reminded me to mention in my original post im running lununtu natty 32bit.

Its a bit of a long process but if nobody else chimes in in the next couple of hours i think i will upgrade to Lubuntu Oneric.

Did you mean PCManFM is the automatic file handler on a Lubuntu Oneric default install?

And what bit os are you using?

---

### Post by aeiah on 2011-12-06
pcmanfm is the default file manager/browser, i believe.

perhaps you could try installing the proprietary oracle java rather than openjdk?

---

### Post by marinara on 2011-12-06
yeah PCManFM is the default file thingy.
I'm using 64 bit, but those extra bits never cause me a problem.

this sounds very similar to your problem.
apparently the guy was trying to use a KDE-compiled app with LXDE

[http://www.google.com/url?sa=t&rct=j&q=lxde%20%20file%20dialog%20won%27t%20open&source=web&cd=4&ved=0CDcQFjAD&url=http%3A%2F%2Fforums.opensuse.org%2Fenglish%2Fget-technical-help-here%2Fapplications%2F463914-help-needed-libreoffice-wont-open-files.html&ei=hhreTsbZCqXy0gHf74CIBw&usg=AFQjCNFND94wyGE0csh_I0-VC1CkBeP-hg&sig2=iBJFoaAgp52amPk4PNE3nw&cad=rja](http://www.google.com/url?sa=t&rct=j&q=lxde%20%20file%20dialog%20won%27t%20open&source=web&cd=4&ved=0CDcQFjAD&url=http%3A%2F%2Fforums.opensuse.org%2Fenglish%2Fget-technical-help-here%2Fapplications%2F463914-help-needed-libreoffice-wont-open-files.html&ei=hhreTsbZCqXy0gHf74CIBw&usg=AFQjCNFND94wyGE0csh_I0-VC1CkBeP-hg&sig2=iBJFoaAgp52amPk4PNE3nw&cad=rja)

---

### Post by davegurn on 2011-12-06
Hey aeiah thanks for the suggestion i will try that now before i go through upgrading and i'm off to check that thread now marinara thanks for the link.

after i have upgraded am i right in thinking the lubuntu oneric install command is

sudo apt-get install lxde

---

### Post by davegurn on 2011-12-06
Oh and marinara

when you checked the two sites what internet browser,java and java internet plugin where you using.

Thanks for the help :)

---

### Post by davegurn on 2011-12-06
Nope marinara

i have upgraded to oneric and pcmanfm is my default file manager. ive installed openjdk and icedtea for mozilla firefox.

Can anyone else think what im missing to enable firefox to recognize through the java uploader where to find my files and display the [COLOR=Red]**browse files**[/COLOR] button?

---

### Post by oldtimer7777 on 2011-12-06
use the latest JRE 1.7 instead from here:

[https://debianhelp.wordpress.com/2011/11/13/how-to-install-sun-java-se-1-7/](https://debianhelp.wordpress.com/2011/11/13/how-to-install-sun-java-se-1-7/)

And don't forget to disable icedtea plugin in mozilla when you done.. It is part of the above linked instructions as well so no worries.. 

> **davegurn said:**
> Hi Everyone 

You have already helped me without knowing through google and the ubuntu forums search feature and i hope to be able to help in the future after i have read some linux books and got used to the switch from windows to linux! But at the moment i am useless at linux :)

Anyway i have purchased a linux vps due to the massive difference in cost to a windows vps and i intend to use it the help with file and video sharing.

i am trying to use the java uploader located here [COLOR=Blue][Putlocker]("http://www.putlocker.com/")[/COLOR] if you click on "upload files now" the upload window will pop up. And also the one here [COLOR=Blue][veehd]("http://veehd.com/")[/COLOR]

Now my problem is that these are the two main video sites i want to upload to but they seem to have the same type of uploader that does not display a "**[COLOR=red]browse files button[/COLOR]**" on linux but does on windows 7! (so in linux i cant seem to add files to the uploader) Also alot of the other video sites have the same type of uploader and seem to have the same proplem. So if i cannot resolve this i cant upload to the popular video sites and my vps will be unable to do what i purchased it for.

I have uploaded 4 screen shots of the veehd and putlockers uploaders [COLOR=Blue][Here]("http://imageshack.us/g/804/windows7putlockerexampl.png/")[/COLOR]

The first two are on windows 7 seven (where there is a[COLOR=red] browse files button[/COLOR]) and the second two are on ubuntu lxde (where the option to [COLOR=red]browse files[/COLOR] has disappeared.)

So finally lol my question is can i do anything about this or are these sites just purely incompatible with linux?

Heres what ive done on my vps so far

1) Installed lxde -> sudo apt-get install lxde

2) Installed Mozilla Firefox -> sudo apt-get install firefox

3) Installed java -> [COLOR=#4C1130]sudo apt-get install openjdk-6-jre-headless

4) Install Mozilla firefox java icedtea plugin -> sudo apt-get install icedtea6-plugin

and then i checked that icedtea is enabled on firefox.

If anyone is kind enough to offer a solution please could you explain how to do it (ie the sudo code as i am not very good at linux)

Thanks in advance for any help

Oh yeah and i use tightvnc to access the gui and marinara reminded me to mention im running lubuntu natty 32 bit.[/COLOR][COLOR=#4C1130]
[/COLOR]

---

### Post by davegurn on 2011-12-06
Hey oldtimer thanks for finding and linking me to that great tutorial on instaling oracle java.(ive bookmarked that)

Unfortunately i have successfully installed it but the java uploaders still have the same problem.

Any other thoughts?

Thanks for the help

---

### Post by marinara on 2011-12-06
dave, please install another web browser into Lubuntu, from an official repository.  
Then use that second web browser to upload as a temporary workaround.

---

### Post by davegurn on 2011-12-07
Hey marinara

Thanks i have resolved the problem by installing epithany web browser!

i would of liked to get it working with firefox but this is an acceptable work around.

Cheers everyone who chipped in and i will mark this as solved

---

