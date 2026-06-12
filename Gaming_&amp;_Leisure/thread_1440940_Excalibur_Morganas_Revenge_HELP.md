---
title: "Excalibur Morganas Revenge HELP"
date: 2010-03-28
forum: Gaming &amp; Leisure
---

### Post by Rustybolts on 2010-03-28
64bit install
I managed to install Alephone via debs i found at
[https://launchpad.net/~snuxoll/+archive/ppa?field.series_filter=]("https://launchpad.net/%7Esnuxoll/+archive/ppa/+build/675361")
I downloaded emr and extracted it
Opened terminal and pointed it towards emr folder
and typed ```
make
``` and got the following error
```
[ -x /usr/local/bin/alephone ] || ( echo /usr/local/bin/alephone is not executable && false)
/usr/local/bin/alephone is not executable
make: *** [sanity] Error 1
```didn't even get chance to ```
make install
```any ideas?

---

### Post by Rustybolts on 2010-03-29
Does anyone play this game?

---

### Post by jammesz on 2010-04-16
I've got the exact same problem. Only difference is that im doing a 32bit install.

Anyone know how to fix this?

---

### Post by Rustybolts on 2010-04-16
Glad this thread has re-surfaced again hopefully someone who has got this working can help. I really like the look of this one and am hoping to play it.
Website is located [COLOR=Red]>>[/COLOR][COLOR=Magenta][HERE]("http://emr.excaliburworld.com/emr3/index.html")[/COLOR][COLOR=Red]<<[/COLOR] if anyone wants to give it a try.

---

### Post by jammesz on 2010-04-25
Just wanted to let you's know that im still interested in a fix for this and definitely be checking up on this thread when ever theres a reply.

---

### Post by royevans on 2010-05-09
Hey how are you? Alright so I have just downloaded this as well and I had the same problem so I looked at the error and I saw ```
[ -x /usr/local/bin/alephone ] || ( echo /usr/local/bin/alephone is not executable && false)
/usr/local/bin/alephone is not executable
 
``` keyword is "alephone" googled it and the game [aleph one](http://source.bungie.org/index.php/Main_Page) came up, so I downloaded it as well and cd'd to the folder and did a ./config and got ```

configure: error: You need SDL 1.2 to run Aleph One.

```(edited to make post smaller) now I must download SDL so I will edit this post after I have done that.

Alright so I have just spent a good hour looking at the files and here is the list I have come up with:

build files:
```
sudo aptitude install build-essential
```
 SDL things (not sure if this format is right, if not just put them in one by one):
```
sudo aptitude install libsdl1.2debian-all libsdl1.2-dev libsdl-image1.2 libsdl-image1.2-dev libsdl-mixer1.2 libsdl-mixer1.2-dev libsdl-ttf2.0-0 libsdl-ttf2.0-dev libsdl-gfx1.2-4 libsdl-gfx1.2-dev libsdl-net1.2 libsdl-net1.2-dev libsdl-sound1.2 libsdl-sound1.2-dev
```
After all this I started to get a "boost/bind" error so I looked it up on google and got the entire boost setup (again format may be bad):
```
sudo aptitude install libboost-date-time1.33.1 libboost-date-time-dev libboost-dev libboost-filesystem1.33.1 libboost-filesystem-dev libboost-iostreams1.33.1 libboost-iostreams-dev libboost-program-options1.33.1 libboost-program-options-dev libboost-regex1.33.1 libboost-regex-dev libboost-signals1.33.1 libboost-signals-dev libboost-test1.33.1 libboost-test-dev libboost-thread1.33.1 libboost-thread-dev
```

And then I get *another* error looking for LUA's:
```
sudo aptitude install lua50 liblua50 liblua50-dev
``` 

after all this I was able to get to the end of ./configure now I will try make and get back to you.

*ps Respond once you read this so I can know if it worked.

---

### Post by jammesz on 2010-05-10
Hi, thanks for your reply. Unfortunately i've gone over my download limit this month and the internet is very slow so i cant test out your work. Hopefully in a week or so i will be able to.

Anyway i appreciate your help and will get back to you.

---

### Post by royevans on 2010-05-10
Sure, no problem, I am new when it comes the terminal so it was pretty fun figuring this out and I would love to know if it works for you. =]

---

