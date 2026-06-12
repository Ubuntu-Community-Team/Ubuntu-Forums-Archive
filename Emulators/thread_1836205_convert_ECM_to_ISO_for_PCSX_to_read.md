---
title: "convert ECM to ISO for PCSX to read"
date: 2011-08-30
forum: Emulators
---

### Post by troysos on 2011-08-30
Hello, I just installed PCSX PS1 emulator. I have a game file and after I extracted the file it is an ECM image. PCSX needs and ISO or other files to beable to read them. What tool do I need to convert this to something PCSX can read and run? Thank you!

---

### Post by dfreer on 2011-08-30
You need ECM. [http://www.neillcorlett.com/ecm/](http://www.neillcorlett.com/ecm/)

---

### Post by troysos on 2011-08-31
I download this and I'm still not sure how to use it. 
It say 
**bin2iso - Convert CD .BIN to .ISO**


  
Converts CD-ROM .BIN images (including full 2352-byte sectors) into .ISO  format (2048-byte sectors).  Automatically detects mode 1 or 2.  Will  warn if there are any form 2 sectors, which are not convertible.

 Usage: bin2iso [-f] input_file output_file  -f: Force conversion and bypass checks

[SIZE=1]So how do I use it? I don't know what this means.[/SIZE]

---

### Post by troysos on 2011-08-31
Thank you for trying to help me out on something you must see are really easy. I know how to do this on my Windows box but I'm so sick of running to Windows when ever I need to get something done :(

---

### Post by thatguruguy on 2011-08-31
> **troysos said:**
> I download this and I'm still not sure how to use it. 
It say 
**bin2iso - Convert CD .BIN to .ISO**


  
Converts CD-ROM .BIN images (including full 2352-byte sectors) into .ISO  format (2048-byte sectors).  Automatically detects mode 1 or 2.  Will  warn if there are any form 2 sectors, which are not convertible.

 Usage: bin2iso [-f] input_file output_file  -f: Force conversion and bypass checks

[SIZE=1]So how do I use it? I don't know what this means.[/SIZE]

Assuming that you have installed ecm (which you can find in the Software Center or Synaptic), do the following. Open a terminal.  Go to wherever the file is you're trying to convert.  Assuming the name of the file is something like "Fred.ecm", type the following in the terminal:
```
unecm Fred.ecm Fred.iso
```

---

### Post by Moonigan on 2012-03-13
so this is what i got when i tried applying thatguruguy's instructions

```
haroun@harouns-MacBook:~$ /home/haroun/Desktop
bash: /home/haroun/Desktop: Is a directory
haroun@harouns-MacBook:~$ unecm TonyHawksProSkater2.bin.ecm /home/haroun/Desktop/TonyHawksProSkater2.bin.iso
UNECM - Decoder for Error Code Modeler format v1.0
Copyright (C) 2002 Neill Corlett

Decoding TonyHawksProSkater2.bin.ecm to /home/haroun/Desktop/TonyHawksProSkater2.bin.iso.
TonyHawksProSkater2.bin.ecm: No such file or directory

```i've also tried it without the directory put in front i.e ```
unecm TonyHawksProSkater2.bin.ecm TonyHawksProSkater2.bin.iso
```and i've even tried renaming the file umpteen times to not include various characters, removing the .bin extension etc but my inexperience has overcome my perseverance

[edit] oh, and i'm using ubuntu 11.10

---

### Post by dfreer on 2012-03-13
It looks like the problem you are experiencing is failure to correctly use the command line and filesystem. This isn't bad, just inexperience like you have stated.
 
For starters, it appears that you have the unecm command installed. If I understand correctly, the compressed CD image is located on your desktop (the TonyHawksProSkater2.bin.ecm file, henceforth known as the ECM file). You will want to change directory to your desktop.

It appears you attempted to change directory to your desktop in the first command, but didn't read or understand the output. 
```
haroun@harouns-MacBook:~$ /home/haroun/Desktop
bash: /home/haroun/Desktop: Is a directory
```
The second line is an error message, because you have forgotten to include the **cd** command in front of your path. The first command should look like this:
```
**cd** /home/haroun/Desktop
```

Remember, as you type paths into the terminal, attempt to use the Tab-Autocompletion feature to ensure that you do not accidentally type the filename wrong.

If successful, your command prompt should change to look like this:
```
haroun@harouns-MacBook:**~/Desktop**$
```
OR
```
haroun@harouns-MacBook:**/home/haroun/Desktop**$
```
The **~** is shorthand for your home directory, **/home/haroun**. You can use it in commands and paths if you don't wish to bother typing the full path.

Finally, the next command you ran was mostly correct, but since the first failed this one failed as well:
```
haroun@harouns-MacBook:~$ unecm TonyHawksProSkater2.bin.ecm /home/haroun/Desktop/TonyHawksProSkater2.bin.iso
UNECM - Decoder for Error Code Modeler format v1.0
Copyright (C) 2002 Neill Corlett

Decoding TonyHawksProSkater2.bin.ecm to /home/haroun/Desktop/TonyHawksProSkater2.bin.iso.
TonyHawksProSkater2.bin.ecm: No such file or directory
```

You did not need to specify the full path to where you wanted to save your file, the **/home/haroun/Desktop/TonyHawksProSkater2.bin.iso** part. However it doesn't hurt, it just would default to using the current working directory if you left out the **/home/haroun/Desktop/** part. Finally, do not append the .iso extension to the end of the file. Although you might be most familiar with ISO files, which is a type of disc image, there are MANY different types of disc images and you cannot simply change the extension to another format.

It appears that your disc is using the BIN type disc image, as evidenced by the .bin part of the filename. These are commonly bundled with another file with the same name but with a .CUE extension, which isn't always needed. 

You could use the BIN to ISO converter, once you have managed to decompress the ECM image to get the disc image into an ISO format, but there's no point. Playstation emulators for the most part understand the difference between BIN and ISO and do not require you to convert it. Finally, playstation discs generally cannot be accurately represented by the ISO format and may break your game if you try.

Hopefully this wall of text will help!

---

### Post by Moonigan on 2012-03-13
thanks! i do love a bit of thps2 *wipes mist of nostalgia from eyes*

---

### Post by dfreer on 2012-03-27
Did the above instructions help you get your game running? Just wondering...

---

### Post by Moonigan on 2012-04-17
yes!

---

### Post by semnotyfos on 2012-05-11
when i write unecm at the terminal it says command not found although i installed ecm via synaptics..

---

### Post by thatguruguy on 2012-05-11
> **semnotyfos said:**
> when i write unecm at the terminal it says command not found although i installed ecm via synaptics..

1. First of all, make sure you have the "ecm" package, not "gmp-ecm", since they are two different things.
```
sudo apt-get install ecm
```

2. The usage has apparently changed for the newest version of ecm. To convert an .iso file to an .ecm file, you now use ecm-compress, and to convert an .ecm file to an .iso file you use ecm-uncompress. So, to convert a file named "foo.ecm" to "foo.bin", you'd type:
```
ecm-uncompress foo.ecm foo.bin
```

---

### Post by mmuldoor on 2012-05-25
Thanks for the update! I used unecm in 10.04 and I kept typing unecm only to find command not found, and i was like great what have you changed now linux... just when i thought using linux was getting easier, throws a wrench at me. Thank god for forums.

---

### Post by erikthedrink on 2012-06-18
Thanks much!

---

### Post by Erquint on 2013-05-06
Thanks alot.

---

