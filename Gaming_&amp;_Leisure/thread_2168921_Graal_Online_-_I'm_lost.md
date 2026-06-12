---
title: "Graal Online - I'm lost"
date: 2013-08-19
forum: Gaming &amp; Leisure
---

### Post by brandondtaylor on 2013-08-19
I've done search after search, and either I'm not using the right keywords or I'm just too dumb to see the answer. 

I am trying to run Graal Online. I am using Ubuntu 13.04. From what I've read in my searches, I just need to download the .zip file for Graal Online, change it to run as an executable in the file properties, and then double click it and it should install. It doesn't work. I don't know if I'm doing something wrong or there's something else going on. Any help would be greatly appreciated.

I'm a total novice when it comes to Linux. I've used Windows my entire life but a recent issue has caused me to give it up for good and go headlong into Linux, burning every bridge as I go. Most things are easy to figure out, but using the terminal is still pretty scary and I have to search for everything I don't understand yet. It's like relearning how to use a computer all over again.

So please, if anyone could help me out, again, I would greatly appreciate it. Thanks. :)

---

### Post by oldrocker99 on 2013-08-20
I notice that the only Linux file for Grall Online is 64-bit. Is your installation 32-bit? If so, it simply won't run a 64-bit program. 64-bit Linux, with the installation of the ia32-libs package, can run 32-bit programs, but not vice versa.

---

### Post by DarkAmbient on 2013-08-20
Nice, Graal Online (classic) is something I played a lot back in the days, when it still was free. Gotta look into it myself!

About what oldrocker99 said, you can check your arch. with:

```
uname -m
```

If it says x86_64, you got 64-bits.



Don't think of the terminal as somethinga annoying, you'r the one in control. Looking things up is perfectly normal, I do it almost all the time doing when using terminal. Imo the important part is not that you'r able to do/run/solve something, but that you can find out how to do/run/solve something, by searching the web, man-pages, asking like now etc.

EDIT: 

Tried it, downloaded it from here: [Graal - x64 - Linux]("http://www.graalonline.com/playerworlds/downloads/file?name=Graal6_linux64.zip")

Unpack the Graal -file, then started it through the terminal with 

```
./Graal
```

I lacked "SDL Mixer" to be able to play, so installed it:

```
sudo apt-get install libsdl-mixer1.2
```

Started it again and was able to play it.

---

### Post by brandondtaylor on 2013-08-20
> **DarkAmbient said:**
> Nice, Graal Online (classic) is something I played a lot back in the days, when it still was free. Gotta look into it myself!

About what oldrocker99 said, you can check your arch. with:

```
uname -m
```

If it says x86_64, you got 64-bits.



Don't think of the terminal as somethinga annoying, you'r the one in control. Looking things up is perfectly normal, I do it almost all the time doing when using terminal. Imo the important part is not that you'r able to do/run/solve something, but that you can find out how to do/run/solve something, by searching the web, man-pages, asking like now etc.

EDIT: 

Tried it, downloaded it from here: [Graal - x64 - Linux]("http://www.graalonline.com/playerworlds/downloads/file?name=Graal6_linux64.zip")

Unpack the Graal -file, then started it through the terminal with 

```
./Graal
```

I lacked "SDL Mixer" to be able to play, so installed it:

```
sudo apt-get install libsdl-mixer1.2
```

Started it again and was able to play it.

Alright, I did uname -m in the terminal and it replied with i686, so I'm thinking that I have a 32bit OS. However, I read that the 64bit Graal Client has backwards compatibility with 32bit so even if you have 32bit you should still be able to run it. Maybe I read it wrong, I'm not sure.

When I downloaded the file Graal6_Linux64.zip it downloaded to my Downloads folder. I don't know if when I unpack it I have to put it somewhere different for it to run properly, but when I unpacked it I got a little purple square looking file that said Graal. It was an executable so I tried running it, but it only spit out a little file that was named 0001

I went into the terminal again and used the ./Graal command, and at first it said no such file or directory. After some searching I found out I have to be in the directory the file is in so I "cd Downloads" and tried it again, only this time it replied with "cannot execute binary file."

I installed the lib that you used for safe measure, but nothing has changed and I'm still unable to figure out how to get Graal installed.

---

### Post by DarkAmbient on 2013-08-20
Then you'r unable to play Graal like oldrocker99 mentioned, it seems Stefan (the creator of Graal) abandoned 32-bits binaries some time ago. A solution, as found out by searching on this, is to use the flash-version of Graal located on Facebook.

---

### Post by brandondtaylor on 2013-08-20
I figured it out. I was putting this off until I exhausted all other solutions, but I guess it had to be done. Originally when I built my PC I made it for 64 bit operating systems. I originally ran Win 7 64bit. When I switched to Linux (using an already-burnt CD given to me by a friend of a friend) it was a 32bit distribution. I followed instructions on the Ubuntu website about how to create a USB drive you can boot from and installed a 64bit Ubuntu and tried your solution again. It worked!

Everything is running swell now and I owe it all to you, DarkAmbient. You're a real lifesaver! :)

---

### Post by DarkAmbient on 2013-08-20
Glad it worked out for you! And nicely done, it's better to use 64bits systems if you can. :) Don't forget to mark this thread as solved please. Have a good time Graaling ;)

---

