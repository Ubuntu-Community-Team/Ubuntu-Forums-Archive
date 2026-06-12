---
title: "Need help installing game, please"
date: 2012-01-20
forum: Gaming &amp; Leisure
---

### Post by goofey24 on 2012-01-20
I have downloaded the Linux game from: [**http://www.lgdb.org/game/ogs_mahjong**](**http://www.lgdb.org/game/ogs_mahjong**)
I love playing Mahjong!
I have extracted the game but when I try to run it, nothing happens. I am not really that great when it comes to installing these types of files: **file:///home/dawn/Downloads/ogs-mahjong-0.9-linux64.7z** Thanks for any help that can be provided. :p

---

### Post by drmrgd on 2012-01-20
A .7z file is a new one to me.  Had to look that one up.  I'm not sure where you're stuck, but try this:

1. Install p7zip in order to decompress the package
```
sudo apt-get install p7zip
```

2. Once you've installed that, run this command on the package to uncompress it:
```
p7zip -d ogs-mahjong-0.9-linux64.7z
```

Once you've done that, you should be able to run the program by running the mj file in there.

Hope that helps

---

### Post by goofey24 on 2012-01-20
> **drmrgd said:**
> 

2. Once you've installed that, run this command on the package to uncompress it:
```
p7zip -d ogs-mahjong-0.9-linux64.7z
```

Once you've done that, you should be able to run the program by running the mj file in there.

Hope that helps
Thanks for that.
Do I needt to cd to where it's extracted to?
I ran the second command and got:

```
7-Zip (A) [64] 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18
p7zip Version 9.20 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,2 CPUs)


Error:
there is no such archive

```

---

### Post by drmrgd on 2012-01-20
> **goofey24 said:**
> Thanks for that.
Do I needt to cd to where it's extracted to?
I ran the second command and got:

```
7-Zip (A) [64] 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18
p7zip Version 9.20 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,2 CPUs)


Error:
there is no such archive

```

Yes, you'd need to be in the same directory as the .7z file for it to work.

---

### Post by goofey24 on 2012-01-20
Thanks, but I am not having any luck. I really hate .zip files and such as I can NEVER get them to install correctly no matter how much I read up on doing so:(

---

### Post by drmrgd on 2012-01-20
Are you still getting the same "there is no archive" error?  Also, are you sure this is the correct file name for the archive:

> ogs-mahjong-0.9-linux64.7z

When I was exploring, I only saw version 0.8.  I didn't think twice about it and copied your version 0.9, though, since I didn't look around for the latest version.  Just to be sure I'm looking at the same thing you're looking at, would you mind posing the output (in code tags) of 

```
ls -l /home/dawn/Downloads/ogs*
```

---

### Post by goofey24 on 2012-01-20
Thanks
here ya go :)
```
 ls -l /home/dawn/Downloads/ogs*
-rw-r--r-- 1 dawn dawn 46841891 Jan 20 08:15 /home/dawn/Downloads/ogs-mahjong-0.9-linux64 (1).7z
```

---

### Post by drmrgd on 2012-01-20
OK, cool.  Looks like it's just a filename issue.  Try this:

```
mv "ogs-mahjong-0.9-linux64 (1).7z" ogs-mahjong-0.9-linux64.7z
```

Just so you'll have a little easier time with the folder name in future.  Then run:

```
p7zip -d ogs-mahjong-0.9-linux64.7z
```

---

### Post by goofey24 on 2012-01-20
I am glad your sticking in there with me, thanks
here is what spat out at me using the 'code':

```
mv "ogs-mahjong-0.9-linux64 (1).7z" ogs-mahjong-0.9-linux64.7z
mv: cannot stat `ogs-mahjong-0.9-linux64 (1).7z': No such file or directory
```

---

### Post by drmrgd on 2012-01-20
Hmmm....are you definitely in the same directory as the ogs-mahjong-0.9-linux64 (1).7z file?  You can also try it with autocompletion by just typing the first few letters of the filename followed by the Tab key, which should fill the rest in (just in case I'm copying the filename down wrong):

```
mv ogs-mah <hit tab to fill in the name> ogs-mahjong-0.9-linux64.7z
```

---

### Post by Soulcage on 2012-01-20
You can always double click on any archive to have it open in file-roller, then extract using that.

---

### Post by goofey24 on 2012-01-20
> **drmrgd said:**
> Hmmm....are you definitely in the same directory as the ogs-mahjong-0.9-linux64 (1).7z file?  You can also try it with autocompletion by just typing the first few letters of the filename followed by the Tab key, which should fill the rest in (just in case I'm copying the filename down wrong):

```
mv ogs-mah <hit tab to fill in the name> ogs-mahjong-0.9-linux64.7z
```
Getting this with what you requested:
 ```
[B]mv ogs-mahjong-0.9-linux64/
mv: missing destination file operand after `ogs-mahjong-0.9-linux64/'[/B]
```

---

### Post by goofey24 on 2012-01-20
> **Soulcage said:**
> You can always double click on any archive to have it open in file-roller, then extract using that.

Have also tried that and get absolutely nothing.
Thanks for all the suggestions.

---

### Post by drmrgd on 2012-01-23
> **goofey24 said:**
> Getting this with what you requested:
 ```
[B]mv ogs-mahjong-0.9-linux64/
mv: missing destination file operand after `ogs-mahjong-0.9-linux64/'[/B]
```

I'm a little confused on what you've got now.  First, the error you got was because you didn't list what you'd like the new file name to be.  The syntax is:

```
mv <original_file_name> <new_file_name>
```

However, if you did use tab-completion in the command that you entered and ended up with > ogs-mahjong-0.9-linux64/ then it suggests that you've already uncompressed the archive.  Did you use tab-completion to get the error that you got, or did you type out the name?  When you goto the directory where the folder is and type:

```
ls -l
```

is the text color red or blue for that file, and do you see a trailing slash (/) after it or no?  If it's blue and/or there's a trailing slash listed after it, then I think you've successfully uncompressed it, and should be able to get into the directory to run it:

```
cd ogs-mahjong-0.9-linux64/
```

followed by 
```
./mj
```

to run it.

---

### Post by drmrgd on 2012-01-23
> **Soulcage said:**
> You can always double click on any archive to have it open in file-roller, then extract using that.

Unfortunately, in this case it doesn't work since p7zip is needed to extract the archive, and p7zip is not the native archive tool in Ubuntu.

---

### Post by goofey24 on 2012-01-23
Text is blue.
This is what is coming up with your codes provided, (thank you very much)

```
./lib/mj-bin: error while loading shared libraries: libopenal.so.1: cannot open shared object file: No such file or directory
```
maybe this output will shed some light on issue.
thanks for not giving up :)

---

### Post by drmrgd on 2012-01-23
> **goofey24 said:**
> Text is blue.
This is what is coming up with your codes provided, (thank you very much)

```
./lib/mj-bin: error while loading shared libraries: libopenal.so.1: cannot open shared object file: No such file or directory
```
maybe this output will shed some light on issue.
thanks for not giving up :)

OK, looks like we're close.  It looks to me like you were successful at decompressing the archive and are now stuck running the program.  

To me it looks like you're missing the OpenAl libraries needed to run the program.  I thought they were part of the native install, but either I'm misdiagnosing the problem or am mistaken about them being part of the system by default.  In any case, you can check and download them by running:

```
sudo apt-get install libopenal1 libopenal-dev
```

Please run that and report back what you got.

---

### Post by goofey24 on 2012-01-23
I think they installed:
```
The following NEW packages will be installed:
  libopenal-data{a} libopenal-dev libopenal1 
0 packages upgraded, 3 newly installed, 0 to remove and 11 not upgraded.
Need to get 0 B/165 kB of archives. After unpacking 543 kB will be used.
Do you want to continue? [Y/n/?] Y
Selecting previously unselected package libopenal-data.
(Reading database ... 208015 files and directories currently installed.)
Unpacking libopenal-data (from .../libopenal-data_1%3a1.13-4_all.deb) ...
Selecting previously unselected package libopenal1.
Unpacking libopenal1 (from .../libopenal1_1%3a1.13-4_amd64.deb) ...
Selecting previously unselected package libopenal-dev.
Unpacking libopenal-dev (from .../libopenal-dev_1%3a1.13-4_amd64.deb) ...
Setting up libopenal-data (1:1.13-4) ...
Setting up libopenal1 (1:1.13-4) ...
Setting up libopenal-dev (1:1.13-4) .
```
then I ran your other commands:
```
ogs-mahjong-0.9-linux64# ./mj
./lib/mj-bin: error while loading shared libraries: **libfreeimage.so.3**: cannot open shared object file: No such file or directory
```
EDIT: ok, got it now. Had to install **libfreeimage.so.3**
Game is now running.
I am really glad you hung in there with me and YOU helped so much :D:D

---

### Post by drmrgd on 2012-01-24
Excellent!  Glad we were able to work it out.  Enjoy!

---

