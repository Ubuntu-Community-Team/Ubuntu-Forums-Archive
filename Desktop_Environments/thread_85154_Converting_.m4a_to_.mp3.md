---
title: "Converting *.m4a to *.mp3?"
date: 2005-11-01
forum: Desktop Environments
---

### Post by YourSurrogateGod on 2005-11-01
Anyone know how to do that? For some reason XMMS doesn't like the *.m4a file format (I can't add it to my list), how can I conver it to a *.mp3 format? Or even *.ogg?

---

### Post by magicfab on 2005-11-01
1. Make sure the multiverse repository is active. See:
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

2. Install faad and lame packages using synpatic or simply typing this in command line:
sudo apt-get install faad lame

3. Follow the instructions at this site (except for the install of packages part) to create a script to convert all files in a directory:
[http://www.togaware.com/linux/survivor/m4a_mp3.shtml](http://www.togaware.com/linux/survivor/m4a_mp3.shtml)

Another way:
[http://www.linuxquestions.org/questions/history/170553](http://www.linuxquestions.org/questions/history/170553)

By all means come back and report to the forum if it worked for you.

---

### Post by YourSurrogateGod on 2005-11-09
This is awesome, thank you! If I use the below script, then I could convert the files to *.ogg format as well, thanks :D .
```
for i in *.m4a
do
  base=`basename "$i" .m4a`
  faad -o - "$i" | lame -h -b 192 - "$base.ogg"
done
```

---

### Post by YourSurrogateGod on 2005-11-12
Just curious, but how would one convert a *.mp3 to a *.ogg? I've tried the below script, but it didn't do the trick.
```
for i in *.mp3
do
  base=`basename "$i" .mp3`
  faad -o - "$i" | lame -h -b 192 - "$base.ogg"
done
```

---

### Post by salva on 2005-11-12
you need to use oggenc instead of lame for the encoding part

---

### Post by YourSurrogateGod on 2005-11-12
[QUOTE=salva]you need to use oggenc instead of lame for the encoding part[/QUOTE]
I can't seem to find it in synap... weird.

---

### Post by Sykil on 2005-11-12
It comes with vorbis-tools.
```
sudo apt-get intall vorbis-tools
```

---

### Post by salva on 2005-11-12
ahh sry... my bad, i should have checked. You will find oggenc in the vorbis-tools package

---

### Post by YourSurrogateGod on 2005-11-12
How would I access the oggenc in the vorbis tool package after I installed it?

---

### Post by salva on 2005-11-13
it should be available to you from the commandline or from a script.
You should be able to modify the script you were using above to use oggenc instead of lame for encoding.
Also if you want to convert from mp3 to ogg you should use lame to decode with, not faad. 

And on a side note.. there is a package in the repositories called mp32ogg that handles the converting. I havent tried it but i supose it gets the job done.....

;)

---

### Post by YourSurrogateGod on 2005-11-13
[QUOTE=salva]it should be available to you from the commandline or from a script.
You should be able to modify the script you were using above to use oggenc instead of lame for encoding.
Also if you want to convert from mp3 to ogg you should use lame to decode with, not faad. 

And on a side note.. there is a package in the repositories called mp32ogg that handles the converting. I havent tried it but i supose it gets the job done.....

;)[/QUOTE]
Thanks, I'll try that and see what results I get.

---

### Post by YourSurrogateGod on 2005-11-13
[QUOTE=salva]And on a side note.. there is a package in the repositories called mp32ogg that handles the converting. I havent tried it but i supose it gets the job done.....[/QUOTE]
This works quite well, thanks.

---

