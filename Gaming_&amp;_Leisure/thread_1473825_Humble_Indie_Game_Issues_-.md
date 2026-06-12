---
title: "Humble Indie Game Issues :-/"
date: 2010-05-05
forum: Gaming &amp; Leisure
---

### Post by beastrace91 on 2010-05-05
So I just downloaded and installed the humble indie game pack and I am having the following issues -

**Lugaru** - I have zero audio, I found a thread that suggested I launch the game with the command **padsp /home/jeff/lugaru/lugaru** however I still get the following output and zero sound when I launch it in this manner: ```
jeff@sager-lintop:~/Downloads$ padsp /home/jeff/lugaru/lugaru
open /dev/[sound/]dsp: Device or resource busy
open /dev/[sound/]dsp: Device or resource busy
open /dev/[sound/]dsp: Device or resource busy

``` Any idea what to do with this one? I am running it on Kubuntu 10.04 32bit

**Gish** - Just gives me a boxy white screen... Input? I have tried this on Kubuntu 10.04 32bit, with an nVidia graphics card and on Ubuntu 9.10 which has the dreaded GMA500 card in it. I know 3D/2D works on both systems from other applications.

~Jeff Hoogland

---

### Post by K.L. on 2010-05-05
I'm running Kubuntu 10.04 64-bit. To run Gish I had to open up terminal, change to Gish's directory and type:

```
./gish
```

I hope it helps.

---

### Post by beastrace91 on 2010-05-05
Ahh alrighty - that works for Gish. I had created a symlink of the gish file in /usr/bin and was trying to launch it simply by running the command **gish**

~Jeff

---

### Post by Perfect Storm on 2010-05-05
A simple;
sh -c "cd <distination> && ./<binary>"
would do the trick.

---

### Post by beastrace91 on 2010-05-06
In case anyone else has the sound issue I had with Lugaru fix it by opening the **/etc/openal/alsoft.conf** file and uncomment the line that has **drivers=** in it.

Regards,
~Jeff

---

### Post by colnizster on 2010-05-06
Hi guys.

When I run gish with ./gish from terminal I get this output:

desktop:~/Games/gish153$ ./gish
./gish: 1: Syntax error: Unterminated quoted string

any ideas?

---

### Post by beastrace91 on 2010-05-06
Operating system/bitage/version?

~Jeff

---

### Post by ELD on 2010-05-06
> **colnizster said:**
> Hi guys.

When I run gish with ./gish from terminal I get this output:

desktop:~/Games/gish153$ ./gish
./gish: 1: Syntax error: Unterminated quoted string

any ideas?

Just wandering but why is there a dollar sign on the end of the gish folder? Is that supposed to be there?

---

### Post by Perfect Storm on 2010-05-06
> **ELD said:**
> Just wandering but why is there a dollar sign on the end of the gish folder? Is that supposed to be there?

$ = user
# = root

---

### Post by ELD on 2010-05-06
> **Artificial Intelligence said:**
> $ = user
# = root

Gotchya cheers, I'm not too awake right now...

---

### Post by Wilbefast on 2010-05-07
I've had a few problems myself - here's what I did to fix them. Maybe this could help you too?
[U][B]
World of Goo[/B][/U]
Installed with DEB file, works perfectly.

_**Lugaru HD**_
No sound. Run the game with "pasuspender" - replace the default command with:

```
pasuspender "/home/william/lugaru/lugaru"
```_**Gish**_
2 errors here. 

First up the game wouldn't run because of a missing library "libopenal.so.0". This can be fixed by creating a symbolic linked to "libopenal.so.1" called "libopenal.so.0", which effectively redirects the requests to the correct library:```
sudo ln -s /usr/lib32/libopenal.so.1 /usr/lib32/libopenal.so.0
```Secondly, there were problems with the sound - a buzzing at first and then nothing after a little while? Running with "pasuspender" directly causes the game to freeze when you try to exit

Create a file called '.asoundrc' in your home folder, with this inside it:
```
pcm.!default {
    @func refer
    name { @func concat
           strings [ "pcm."
                     { @func getenv
                       vars [ ALSA_DEFAULT_PCM ]
                       default "pulse"
                     }
         }
}

pcm.pulse { type pulse }
ctl.pulse {
    type pulse
#   source "Monitor of HDA Intel"
}
```Then run the game with the following script from the give folder, using the following command:

```
pasuspender $(ALSA_DEFAULT_PCM=hw:0 ./gish)
```Thanks to **[Spudd86]("http://achrongame.com/forums/viewtopic.php?f=27&t=977")** for this fix.

_**Penumbra**_
Painful intermittent buzzing sound. Neither a direct "pasuspender" nor the above technique works, so in the game menu, go through **options > sound > output** and choose **"OSS Software"**. This seems to fix the problem.

[U][B]Aquaria
[/B][/U]Installs and runs fine out of the box.

---

### Post by colnizster on 2010-05-07
thanks to everyone for the info. 

Wilbefast: I followed your instructions and I am still having trouble running gish. 

I am running ubuntu 9.10 32bit.

here are some terminal outputs:

desktop:~/Games/gish153$ sudo pasuspender $(ALSA_DEFAULT_PCM=hw:0 ./gish)
bash: ./gish: cannot execute binary file
pasuspender [options] ... 

  -h, --help                            Show this help
      --version                         Show version
  -s, --server=SERVER                   The name of the server to connect to


and


desktop:~/Games/gish153$ sudo ./gish
./gish: 1: Syntax error: Unterminated quoted string


any help much appreciated

---

### Post by colnizster on 2010-05-07
so I figured out what was wrong and got gish working (yay!)

the first time I downloaded gish and untarred it there was only one executable file inside - gish

i googled the "unterminated quote string error" and found that this can be caused by trying to run a 64bit program using a 32bit OS

i re-downloaded the gish tarball from wolfire today and it included two gish executables - gish and gish64 - so apparently the download from the other day was just the 64bit.

---

