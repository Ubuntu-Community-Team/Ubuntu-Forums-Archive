---
title: "Google Earth 5.0 trouble"
date: 2009-02-02
forum: General Help
---

### Post by TonKi on 2009-02-02
So I had to install GoogleEarth 5.0, downloaded the .bin and run the installation. (tried both as sudo and user)
When I now start up I alwasy get this ```
./googleearth-bin: 
relocation error: /usr/lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, 
version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference

```

and when installed as sudo I get the same but I locks itself out of the config (yes, I did not start it from the installation)```
$ googleearth 
/usr/lib/googleearth/googleearth-bin: relocation error:
/usr/lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, 
version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 
with link time reference
$ googleearth 
Warning: Unable to create prefs directory '/home/stylesp/.googleearth'. File exists.
/usr/lib/googleearth/googleearth-bin: relocation error:
/usr/lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, 
version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 
with link time reference

```
then I remove the directory and can start again.

Im on intrepid, Desktop effect disabled right now.
btw also tried it with make-googleearth-package --force

Any ideas :popcorn:

---

### Post by elcorazon on 2009-02-02
Hi,

I had the same problem and just after reading your post I solved the problem :-)

Simply rename the libcrypto.so.0.9.8 in the google-earth install dir to something else, so the libcrypto installed on the system is used.

Works fine for me

---

### Post by B.Blackbird on 2009-02-02
> **elcorazon said:**
> Hi,

I had the same problem and just after reading your post I solved the problem :-)

Simply rename the libcrypto.so.0.9.8 in the google-earth install dir to something else, so the libcrypto installed on the system is used.

Works fine for me


Thank you, works great! :)

---

### Post by yellerKat on 2009-02-02
And thank you from me!

---

### Post by Dalston on 2009-02-02
> **elcorazon said:**
> Hi,

I had the same problem and just after reading your post I solved the problem :-)

Simply rename the libcrypto.so.0.9.8 in the google-earth install dir to something else, so the libcrypto installed on the system is used.

Works fine for me

Thanks that worked for me.

---

### Post by agim on 2009-02-02
And for me as well! Thanks a lot, really wanted to try this.

Out of curiosity, where did you find this?

---

### Post by Ron F. on 2009-02-02
It works for me too. I would be concerned however, for anyone not familiar with Linux, attempting to use Ubuntu as a newbie, and then running into this problem.

-Ron

---

### Post by meitetsuman on 2009-02-02
Yes, I'm a newbie. Tried to download GoogleEarth 5.0. It automatically chose the Linux version for me, but when I try to launch it, it won't launch. I have a Wubi installation, if that makes a difference.

---

### Post by MichaelSM on 2009-02-02
Having similar problems.

'Simply rename the libcrypto.so.0.9.8 in the google-earth install dir to something else, so the libcrypto installed on the system is used.'

How do we accomplish this?

Mike.

---

### Post by sslewis on 2009-02-03
Here's what worked for me on Intrepid..

- Download GoogleEarthLinux.bin to desktop.
- Open terminal and enter the following commands:
```

$ cd Desktop
$ sudo su
# chmod +x GoogleEarthLinux.bin
# ./GoogleEarthLinux.bin

```

- The program installed under opt/google-earth
- In that folder renamed libcrypto.so.0.9.8 as sudo and all is well.

Thanks for the help gang.

---

### Post by hakvoort on 2009-02-03
thanks, this solved my problem:p

---

### Post by autonomouse on 2009-02-03
worked for me too. I dunno why it worked, but it did :-)

---

### Post by unprinted on 2009-02-03
> **elcorazon said:**
> Hi,
Simply rename the libcrypto.so.0.9.8 in the google-earth install dir to something else, so the libcrypto installed on the system is used.

.. and another thanks for this.

---

### Post by elcorazon on 2009-02-03
> **MichaelSM said:**
> Having similar problems.

'Simply rename the libcrypto.so.0.9.8 in the google-earth install dir to something else, so the libcrypto installed on the system is used.'

How do we accomplish this?

Mike.

Depends on the installation directory of google-earth. Mine is /opt/google-earth, I think if you installed as root it might be /usr/local/googleearth
```
sudo su -
cd /usr/local/googleearth
mv libcrypto.so.0.9.8 libcrypto.so.0.9.8.bak
```
Voila!

> **agim said:**
> And for me as well! Thanks a lot, really wanted to try this.

Out of curiosity, where did you find this?
By default the binary links against libraries inside the same directory and if there is none the binary is linked against libraries in the library path (like /usr/lib and others)
The libcrypto shipped with google-earth obviously was linked against another version of libssl than the one installed in Ubuntu. And by renaming the libcrypto-file the one of the system is used. Allright? :confused:

---

### Post by meitetsuman on 2009-02-04
It's not working for me. I'm probably doing something stupid. Here's what happened:
owner@owner-desktop:~$ $ cd Desktop
bash: $: command not found
owner@owner-desktop:~$ $ sudo su
bash: $: command not found
owner@owner-desktop:~$ # chmod +x GoogleEarthLinux.bin
owner@owner-desktop:~$ # ./GoogleEarthLinux.binsudo su -
owner@owner-desktop:~$ cd /usr/local/googleearth
bash: cd: /usr/local/googleearth: No such file or directory
owner@owner-desktop:~$ mv libcrypto.so.0.9.8 libcrypto.so.0.9.8.bak

Any suggestions? I have no idea what any of this means.

---

### Post by jacksaff on 2009-02-04
You don't type the $ and # signs. They are already there in the terminal prompt. 

$ means the prompt in the terminal is for a normal user. # means the terminal session is running for a root user. You will see the symbol there yourself in the terminal.

When you run the 'sudo su' command your terminal session turns into a root-user session and the prompt is changed to # to remind you of this.

---

### Post by sirhceel23 on 2009-02-04
Well got Google Earth to finally run but the Cache is all messed up, causes some serious issues running the program.  I get this error: ```
Could not create directory:

/root/.googleearth/Cache
```

Press Ok then I get: 
```
Google Earth could not write to the current cache or myplaces file location. The values will be set as follows:
My Places Path: "/home/chris/.googleearth"
Cache Path: "/home/chris/.googleearth/Cache"
```

Any idea's my oh so amazing Ubuntu gods?

Ok maybe just really cool tiki idols...;)

---

### Post by sirhceel23 on 2009-02-04
Well tells you your giving it the wrong file path, check your path. It varies, mine was in /opt/googleearth. That got mine running but still working on some cache problems. Hope you have better luck! 


> It's not working for me. I'm probably doing something stupid. Here's what happened:
owner@owner-desktop:~$ $ cd Desktop
bash: $: command not found
owner@owner-desktop:~$ $ sudo su
bash: $: command not found
owner@owner-desktop:~$ # chmod +x GoogleEarthLinux.bin
owner@owner-desktop:~$ # ./GoogleEarthLinux.binsudo su -
owner@owner-desktop:~$ cd /usr/local/googleearth
bash: cd: /usr/local/googleearth: No such file or directory
owner@owner-desktop:~$ mv libcrypto.so.0.9.8 libcrypto.so.0.9.8.bak

Any suggestions? I have no idea what any of this means.

---

### Post by zerubbabel on 2009-02-04
I'm running Intrepid on a Dell Latitude d830 with the Intel graphics chip, and Google Earth runs, but the image is messed up. Some sections begin to display right, but then are overwritten with chaos. Also letters are missing from the text that overlays the image.

---

### Post by TonKi on 2009-02-04
already said
have to change my forum view back ;)

---

### Post by kystorms on 2009-02-04
> **sslewis said:**
> Here's what worked for me on Intrepid..

- Download GoogleEarthLinux.bin to desktop.
- Open terminal and enter the following commands:
```

$ cd Desktop
$ sudo su
# chmod +x GoogleEarthLinux.bin
# ./GoogleEarthLinux.bin

```

- The program installed under opt/google-earth
- In that folder renamed libcrypto.so.0.9.8 as sudo and all is well.

Thanks for the help gang.

question.....

how do we  rename the folder/file? I can not seem to locate it using terminal, tho I see it in the file browswer. I just have no access in the file browser to it.

thank you for any help

---

### Post by EoRaptor013 on 2009-02-04
Works, but Google Earth will only contact the GE server if I run it sudo. I don't like running things sudo, but I don't know what to change to get it right. 
Thanks. 
Randy

---

### Post by ruffneck on 2009-02-05
Thanks elcorazon!

---

### Post by DougieFresh4U on 2009-02-05
> **sslewis said:**
> Here's what worked for me on Intrepid..

- Download GoogleEarthLinux.bin to desktop.
- Open terminal and enter the following commands:
```

$ cd Desktop
$ sudo su
# chmod +x GoogleEarthLinux.bin
# ./GoogleEarthLinux.bin

```

- The program installed under opt/google-earth
- In that folder renamed libcrypto.so.0.9.8 as sudo and all is well.

Thanks for the help gang.

This method worked excellent for me. 
Didn't have to edit any thing, just ran it through terminal as posted in this post and went to Applications>Internet>Google Earth  and it opened up beautifully .
Thanks

---

### Post by meitetsuman on 2009-02-05
Well, I'm still hacking away at this:

owner@owner-desktop:~$ cd desktop
bash: cd: desktop: No such file or directory
owner@owner-desktop:~$ sudo su
[sudo] password for owner: 
root@owner-desktop:/home/owner# chmod +x GoogleEarthLinux.bin
chmod: cannot access `GoogleEarthLinux.bin': No such file or directory
root@owner-desktop:/home/owner#

The file is sitting on my desktop! I can see it!

---

### Post by Denny Johnson on 2009-02-06
> **DougieFresh4U said:**
> This method worked excellent for me. 
Didn't have to edit any thing, just ran it through terminal as posted in this post and went to Applications>Internet>Google Earth  and it opened up beautifully .
Thanks

X2  [Hardy].............Thanks

---

### Post by bethnesbitt on 2009-02-08
If you want to get rid of the message cannot right to cache /root/.googleearth just open up a terminal and type

sudo chown -R username:username /root/.googleearth/
sudo chmod 777 username:username /root/.googleearth/

---

### Post by DeMus on 2009-02-08
> **elcorazon said:**
> Hi,

I had the same problem and just after reading your post I solved the problem :-)

Simply rename the libcrypto.so.0.9.8 in the google-earth install dir to something else, so the libcrypto installed on the system is used.

Works fine for me

I would call it a gigantic bug from Google's side. It also works for me so I can use the program.
How the hell did you figure this out? Where did you find the solution?

---

### Post by antony_css on 2009-02-09
Me too... :(

Is it because I am using an old version of ubuntu (hardy)?

Anyway, many thanks for your contribution

---

### Post by remo99 on 2009-02-09
re Google 5.0 trouble

I also dnldd google earth 5.0 and had trouble opening it-it would open then close.  I took the advise of one of the posters and it started working. what I did was to go into my "home/greg" folder, found the folder "google-earth" opened it up, went to the file named "ibcrypto.so.0.9.8" then renamed it to "ibcrypto.so.0.9.8old" by right clicking on it and selecting rename.  Then I went to the desktop and clicked on the googleearth icon and it opened up

hope that helped

God bless  greg

---

### Post by macozz on 2009-02-11
I follow the instructions posted here. GE opens and keep open, but even if I install it as a normal user (in my home folder) if I execute it as single user it does no show anything and I cannot change any setting. If I run it as root (with sudo ./googleearth) it works fine (if I disable atmosphere, otherwise is dam slow!). Any ideas why this?
Thanks.

My system: Eeepc 1000H, 16Gb HD, 2Gb RAM, Ubuntu 8.10 with Adam's kernel, lean, no Compiz.

---

### Post by paris_alex on 2009-02-11
Guys,

looks like Google Earth 5.0 is no longer in beta (still on beta last nite when i checked). 

so, my question is... can i install it via apt-get install? i already have medibuntu and google's s/w sources added.

...any idea when (roughly) google earth will make its way into one of these repository?

---

### Post by zerubbabel on 2009-02-12
I got past the problem of the earth image that looked like random noise by disabling Compiz, but still the fonts are messed up, omitting lots of letters so that it's hard to read the place names.

---

### Post by crunchfighter on 2009-02-13
Try changing:
System->Appearance->Visual Effects-> None.

It works like a champ when I turn off all the fun effects.

I wonder if there is a way to automatically turn off visual effects in the command line every time it runs?

---

### Post by fongjd85 on 2009-02-14
Instead of renaming the libcrypto.so.0.9.8, why not try upgrading your OPENSSL_0.9.8?  This worked for me.  I would not call this a major bug on Google's part.  You just need to have the newest version of OPENSSL.  Hope this helps!

---

### Post by fakhriz on 2009-02-14
> **fongjd85 said:**
> Instead of renaming the libcrypto.so.0.9.8, why not try upgrading your OPENSSL_0.9.8?  This worked for me.  I would not call this a major bug on Google's part.  You just need to have the newest version of OPENSSL.  Hope this helps!

How can I upgrade my OPENSSL? 

btw, I did rename it but didn't work :(

---

### Post by macozz on 2009-02-15
somebody else experience the problem of no contection to server as normal user, but only as sudo?
If so, do you solved it? How?
Thanks

---

### Post by zerubbabel on 2009-02-15
Even with visual effects set to None, the fonts are messed up.

---

### Post by benhur99ph on 2009-02-16
> **zerubbabel said:**
> Even with visual effects set to None, the fonts are messed up.

Yeah. I turned off all effects too but there are still missing letters. Somebody, please help us with this.

---

### Post by davgard on 2009-02-16
Hey,
    I was having the same problem, i tried your solution and presto chango, just like magic it works!!!!! :-)  thanks for your help..

---

### Post by dreamdigital on 2009-02-17
Help, can't figure this out.  I installed Google Earth 5.0 ok, but when I try to open it, it just crashes on me.  It opens almost then as soon as I see the tips at start up it just crashes and I get no error message or anything.  Can't figure out how to fix this.

---

### Post by dreamdigital on 2009-02-17
That didn't work for me, still crashes right when it starts to load up

---

### Post by crunchfighter on 2009-02-17
> **dreamdigital said:**
> Help, can't figure this out.  I installed Google Earth 5.0 ok, but when I try to open it, it just crashes on me.  It opens almost then as soon as I see the tips at start up it just crashes and I get no error message or anything.  Can't figure out how to fix this.

That's exactly what mine was doing.  My solution was to turn off the visual effects in Preferences->Appearance->Visual Effects->None.

Do you have compiz or emerald running?  If so, they appear to be in compatible.  Probably just too much going on for the video cards.

---

### Post by earthpigg on 2009-02-17
has anyone tried installing from google's repos to avoid these install issues?

[http://www.google.com/linuxrepositories/apt.html](http://www.google.com/linuxrepositories/apt.html)

google's directions to add their repo to your sources.list sucks, here is that [repogen ]("http://repogen.simplylinux.ch/")returns (and what i have on my install at home):

```
#### Google Linux Software Repositories - http://www.google.com/linuxrepositories/index.html
## Run this command: wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -
deb http://dl.google.com/linux/deb/ stable non-free
```


edit: a better way to turn compiz off and on so you _**dont **_lose your settings:

turn off: alt+f2 and type "metacity --replace"
turn on: alt+f2 and type "compiz --replace"

---

### Post by rohan1 on 2009-02-18
hmmm..I too have the same problem...google aunches and then crashes immediately...tried replacing compiz with metacity..no luck there..

---

### Post by Vaphell on 2009-02-20
try to run it from terminal
googleearth

when it crashes it should leave some error message in terminal

---

### Post by spanky1023 on 2009-02-24
> **sirhceel23 said:**
> Well got Google Earth to finally run but the Cache is all messed up, causes some serious issues running the program.  I get this error: ```
Could not create directory:

/root/.googleearth/Cache
```

Press Ok then I get: 
```
Google Earth could not write to the current cache or myplaces file location. The values will be set as follows:
My Places Path: "/home/chris/.googleearth"
Cache Path: "/home/chris/.googleearth/Cache"
```

Any idea's my oh so amazing Ubuntu gods?

Ok maybe just really cool tiki idols...;)

> **bethnesbitt said:**
> If you want to get rid of the message cannot right to cache /root/.googleearth just open up a terminal and type

sudo chown -R username:username /root/.googleearth/
sudo chmod 777 username:username /root/.googleearth/




im having the same issue!  

i tried the:
sudo chown -R username:username /root/.googleearth/
sudo chmod 777 username:username /root/.googleearth/

and got rid of the above posted message.... but google earth is still not working.
it loads, but it just sits there with a black screen.

any ideas ??

---

### Post by spanky1023 on 2009-02-24
bump . . . .

---

### Post by spanky1023 on 2009-02-25
any help ??  please ??

---

### Post by crunchfighter on 2009-02-26
No luck turning off the visual effects first?

---

### Post by spanky1023 on 2009-02-26
> **crunchfighter said:**
> No luck turning off the visual effects first?

no luck !

---

### Post by Andronos on 2009-03-04
```
$ sudo -s
# cd /opt/gooogle-earth
# mv libcrypto.so.0.9.8 libcrypto.0.9.8~
# ln -s /usr/lib/libcrypto.so.9.8.0 libcrypto.0.9.8
```

That would do the trick for the libcrypto error.

---

### Post by jhmos on 2009-03-09
For the "Could not create directory: /root/.googleerth/Cache" problem, edit your .config/Google/GoogleEarthPlus.conf replacing /root with your home directory for the following two lines:

KMLPath=/root/.googleearth
CachePath=/root/.googleearth/Cache

---

### Post by roach33 on 2009-03-10
Having the same prob - visual effects disabled, with or without proprietary drivers, my system still crashes GE. Should it crash if the system is too slow?

---

### Post by kiwi-pete on 2009-04-29
I get the following error when trying to run from Terminal.

kiwipete@kiwipete-desktop:~$ googleearth
Google Earth has caught signal 11.



Another crash happened while handling crash!

kiwipete@kiwipete-desktop:~$ 

I am so confused, even when I try to run Googleearth from the desktop icon or Applications, it shows the flash screen then shuts down.

---

### Post by nrayever on 2009-04-30
Thanks a lot man! it worked great. :):)

---

### Post by suniyo on 2010-03-04
This really helped me to solve the problem:

[http://www.google.com/support/forum/p/earth/thread?tid=38e1729a9b486887&hl=en](http://www.google.com/support/forum/p/earth/thread?tid=38e1729a9b486887&hl=en)

simple and easy.

---

