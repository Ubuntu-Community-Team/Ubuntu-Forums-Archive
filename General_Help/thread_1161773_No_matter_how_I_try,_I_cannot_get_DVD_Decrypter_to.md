---
title: "No matter how I try, I cannot get DVD Decrypter to work under wine - Need help!!"
date: 2009-05-17
forum: General Help
---

### Post by Mike Margary on 2009-05-17
**[SIZE=3]I am very new to Ubuntu and really want to make it succeed for me – I have to get away from M'soft before I go crazy.[/SIZE]**

 [FONT=Petra][SIZE=3]But – I now find that I really do need some assistance from some kind soul who will take pity on my and get me over the early hurdles I am encountering.[/SIZE][/FONT]
 **[FONT=Petra][SIZE=3]Problem is that I am an old fart (71) and I am finding 'Linux talk' very confusing.[/SIZE][/FONT]**

 **[FONT=Petra][SIZE=3]I have managed to get Firefox, Open Office and Thunderbird working just fine, so I can now do most things that I need – however, there are some things that I wish to have working (as they did in Windows), such as DVD Decrypter.[/SIZE][/FONT]**

 [FONT=Petra][SIZE=3]I found an excellent tutorial on my-guides.net, which was written by axel and I have very carefully tried to follow every step to install DVD Decrypter under wine – but I seem to get nowhere.  Very frustrating.
The tutorial was titled : How to install RipIt4Me, DVDShrink and DVDDecrypter in Linux - Written by axel 
Whenever I enter a command (from the tutorial) into a terminal, I get the following response – regardless of what the command actually is – ie ….. …......
mike@mike-desktop:~$ $ winecfg 
**bash: $: command not found **
- or - 
mike@mike-desktop:~$ 
[/home/mike/.wine/dosdevices/c:/windows/command/start.exe] 
**End-of-central-directory signature not found.  Etc etc etc**
Whatever I do, I just get either of these two 'errors'.
[/SIZE][/FONT][FONT=Petra][SIZE=3]  I'm obviously missing something, but I have no idea what it is!!!![/SIZE][/FONT][FONT=Petra][SIZE=3]
Can anybody please help me through these early (and very trying) steps in getting Ubuntu working?[/SIZE][/FONT]
 **[FONT=Petra][SIZE=3]Any help would be muchly appreciated.[/SIZE][/FONT]**

 **[FONT=Petra][SIZE=3]Mike in Melbourne.[/SIZE][/FONT]**

---

### Post by thegreenblob on 2009-05-17
This may sound like a silly question but is wine installed? (Cause it seems kind of odd that winecfg doesn't work)

What happens when you do:

```
sudo apt-get install wine
```

in the terminal? (Applications --> Accessories --> Terminal)

---

### Post by Mike Margary on 2009-05-17
> **thegreenblob said:**
> This may sound like a silly question but is wine installed? (Cause it seems kind of odd that winecfg doesn't work)

What happens when you do:

```
sudo apt-get install wine
```in the terminal? (Applications --> Accessories --> Terminal)


Hi thegreenblob - thanks for your reply.  ):P
I'm sure that wine is installed, because it shows up under 'Applications'
I can configure wine from there, but it will not recognise my DVD drive.
When I enter the code you have provided in a Terminal, it asks for my password but does not allow me to enter it.
I think I have done something wrong earlier on somehow.
Very confusing.    :confused::confused:
Mike

---

### Post by thegreenblob on 2009-05-17
Oh I think I see your problem with winecfg. I didn't notice the first time I read it but you typed: 

> mike@mike-desktop:~$ $ winecfg 

The $ was what was making it say command not found. It should simply be:

```
winecfg
```

And you should be able to configure your dvd drive from there in the "Drives" tab. And as mine says "E: /media/cdrom" which if that wasn't there I don't think my drive would work. So make sure something like that is there.

If it still doesn't work you may have to set DVD Decrypter to Windows NT 4.0 like the tutorial you mentioned said which you can do that from winecfg too.

EDIT: And about it not letting you enter your password, it is letting you enter it, it just doesn't show you typing it. :P So just type it and hit enter and it will work.

---

### Post by clhsharky on 2009-05-17
dvd::rip

AcidRip

DVD95

Very useful, all from "Add/Remove" under Applications.

---

### Post by thegreenblob on 2009-05-17
> **clhsharky said:**
> dvd::rip

AcidRip

DVD95

Very useful, all from "Add/Remove" under Applications.

Speaking of alternatives, k9copy is a good one too.

---

### Post by Mike Margary on 2009-05-17
Thanks thegreenblob & clhsharky - that helped and I was able to configure wine from the terminal input.  Dunno how that extra $ got in there??  On the question of alternatives to DVD Decrypter, as far as I can tell, none of the alternative apps mentioned will allow copy protection to be removed as will DVD Decrypter.
I've tried them all - but maybe I missed something there too
Mike

---

### Post by Mike Margary on 2009-05-17
It's getting a bit late here in OZ, so it's dinner time and then off to bed for me.  I'll check back in the morning.
Thanks for your efforts so far guys.
Mike

---

### Post by Greenwidth on 2009-05-17
Copy the .exe to:

.wine/drive_c/system32 

which is in your Home folder (CTRL+H to see hidden folders), and run it from there:
right click open with "Wine Windows Program Loader"

---

### Post by thegreenblob on 2009-05-17
> **Mike Margary said:**
> Thanks thegreenblob & clhsharky - that helped and I was able to configure wine from the terminal input.  Dunno how that extra $ got in there??  On the question of alternatives to DVD Decrypter, as far as I can tell, none of the alternative apps mentioned will allow copy protection to be removed as will DVD Decrypter.
I've tried them all - but maybe I missed something there too
Mike

You might need to enable dvd playback before the alternatives will rip a copyright protected dvd. To do so just enter the following 2 commands in a terminal:

```
sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/install-css.sh
```

Credit for that goes to [ubuntuguide]("http://ubuntuguide.org/wiki/Ubuntu:Jaunty#DVD_Playback_Capability") as I always forget how to do that. :)

---

### Post by Mike Margary on 2009-05-17
Hi thegreenblob - thanks for the follow up.
I entered the two commands you suggested in a terminal and got the following result.......
E: Couldn't find package libdvdread3
mike@mike-desktop:~$ sudo /usr/share/doc/libdvdread3/install-css.sh
sudo: /usr/share/doc/libdvdread3/install-css.sh: command not found

I feel a bit like I am wandering around in a very thick fog - no idea of where I am or where to go ......

Do you think I should maybe try re-installing wine and DVD Decrypter to maybe get a clean start on this challenge?
Best
Mike

---

### Post by michy99 on 2009-05-17
If you are using 10.4 Jaunty, I believe that libdvdread4 has replaced libdvdread3.

edit: 9.04, not 10.4.

---

### Post by lisati on 2009-05-17
This is just my personal preference, but I find dvdshrink easier. Not count "bad" burns, there has been only one disk I haven't been able to process with dvdshrink.

---

### Post by lisati on 2009-05-17
> **michy99 said:**
> If you are using 10.4 Jaunty, I believe that libdvdread4 has replaced libdvdread3.

I'm using 9.04 Jaunty, it reports that it can't find libdvdread3. I haven't tried any of the 10.* releases yet.

---

### Post by michy99 on 2009-05-17
Oops, my mind is on the blink. I meant 9.04. Try replacing the libdvdread3 with libdvd4 in the commands.```
sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

