---
title: "File or directory not found"
date: 2006-01-30
forum: Desktop Environments
---

### Post by xinelo on 2006-01-30
I've got a file with a long name in an external HHD. I try to remove it but I get a message that there is no such file and that it can't be removed. However, the file appears when I list. See for yourself:

[email]root@micho:~/sda1/.Trash-xinelo/.zips[/email]# ls
[B][COLOR="Blue"]SesiÃ³n electrO tecNo Pop - fangoRia astrUD la moNja enAnÃ¡ galacTica lemoNfly Ã lma-X eLlos la CostA bravA manO de santO dinarAma chico y chica..
[/COLOR][/B]root@micho:~/sda1/.Trash-xinelo/.zips# ls -ls
total 0
? ?--------- ? ? ? ?                ? [COLOR="Red"]**SesiÃ³n electrO tecNo Pop - fangoRia astrUD la moNja enAnÃ¡ galacTica lemoNfly Ã lma-X eLlos la CostA bravA manO de santO dinarAma chico y chica..**[/COLOR]
[email]root@micho:~/sda1/.Trash-xinelo/.zips[/email]# rm SesiÃ³n\ electrO\ tecNo\ Pop\ -\ fangoRia\ astrUD\ la\ moNja\ enAnÃ¡\ galacTica\ lemoNfly\ Ã lma-X\ eLlos\ la\ CostA\ bravA\ manO\ de\ santO\ dinarAma\ chico\ y\ chica..
**rm: impossible to remove **`SesiÃ³n electrO tecNo Pop - fangoRia astrUD la moNja enAnÃ¡ galacTica lemoNfly Ã lma-X eLlos la CostA bravA manO de santO dinarAma chico y chica..': **No such file or directory**
[email]root@micho:~/sda1/.Trash-xinelo/.zips[/email]# rm -f SesiÃ³n\ electrO\ tecNo\ Pop\ -\ fangoRia\ astrUD\ la\ moNja\ enAnÃ¡\ galacTica\ lemoNfly\ Ã lma-X\ eLlos\ la\ CostA\ bravA\ manO\ de\ santO\ dinarAma\ chico\ y\ chica..
[email]root@micho:~/sda1/.Trash-xinelo/.zips[/email]# ls
[COLOR="Blue"]**SesiÃ³n electrO tecNo Pop - fangoRia astrUD la moNja enAnÃ¡ galacTica lemoNfly Ã lma-X eLlos la CostA bravA manO de santO dinarAma chico y chica..**[/COLOR]

Any clues how I can remove this file? 

Thanks a lot! xinelo

---

### Post by syklitengutt on 2006-01-30
lol take it to a spanish forum or something...
I dont understand anything...

---

### Post by yanik on 2006-01-30
Does nautilus sees it?  or any other file manager?  did you tried with midnight commander (mc) ?

---

### Post by art on 2006-01-30
If you put the file name in quotes, like 

rm "Very Long Filename"

then there should be no problem.

---

### Post by hillbilly on 2006-01-30
> If the name of your file name can be isolated using wild cards like > SesiÃ³n electrO tecNo Pop* then you can delete it using 
> rm SesiÃ³n electrO tecNo Pop*

Hmm..from your ls it looks like the only file in the directory, so you can just do > rm *

NOTE: DO MAKE SURE THAT WHEN THE  WILDCARD EXPANDS, IT DOES NOT INCLUDE OTHER FILE IN YOUR DIRECTORY WHICH COULD GET DELETED

---

### Post by xinelo on 2006-07-31
Thanks for your help, everyone. 

Yanik,  nautilus can see it, so so. When I open the directory that contains it, it is there and I can see it, but when I try to click on the file or select it, it disappears. 

With mignight commander, the problem is the same. It can see just as I can see on the console, but it cannot delete it. 

art, the result is the same if I use quotes, as you suggest. 

hillbilly: that (corrupt?) file being the only file in the directory, I do "(sudo) rm (-f) Sesi*" but the result is exactly the same. Doing "rm *" has exactly the same result. Which is: 

rm: **impossible to remove** `SesiÃ³n electrO tecNo Pop - fangoRia astrUD la moNja enAnÃ¡ galacTica lemoNfly Ã lma-X eLlos la CostA bravA manO de santO dinarAma chico y chica..': **File or directory not found**

[ardchoille]("http://www.ubuntuforums.org/member.php?u=55320") suggested to open a term, run gksu nautilus, browse to the correct Trash bin on the correct device and delete it.

If I do that, I can go to /media/sda1/.Trash-xinelo and delete de .zips directory. However now there is a .Trash-root directory. The .zips directory is there but I can't delete it, not even from the nautilus session opened with gksu.

Then, in the gksudo nautilus window, I tried File -> Empty Trash but I had the same problem.

Precisely, the error message is:

Error "File not found" when deleting "/media/SDA1/...o y chica..".

Weird.

Any other ideas?

---

### Post by ardchoille on 2006-07-31
Is this the only file in that directory? If so, try this:

1. cd to the directory containing the file
2. sudo chown <user>:<user> *
  where <user> is your valid username
3. sudo chmod 640 *
4. sudo rm -r *

The reason I suggest chown and chmod is that it looks like this file has no ownerships or file attributes.

Does this help?

---

### Post by xinelo on 2006-07-31
> xinelo@micho:~/sda1/.Trash-root/.zips$ sudo chown xinelo:xinelo *
chown: impossible to access `SesiÃ³n electrO tecNo Pop - fangoRia astrUD la moNja enAnÃ¡ galacTica lemoNfly Ã lma-X eLlos la CostA bravA manO de santO dinarAma chico y chica..': No such file or directory
xinelo@micho:~/sda1/.Trash-root/.zips$ sudo chmod 640 *
chmod: impossible to access `SesiÃ³n electrO tecNo Pop - fangoRia astrUD la moNja enAnÃ¡ galacTica lemoNfly Ã lma-X eLlos la CostA bravA manO de santO dinarAma chico y chica..': No such file or directory
xinelo@micho:~/sda1/.Trash-root/.zips$ sudo rm -r *
rm: impossible to remove `SesiÃ³n electrO tecNo Pop - fangoRia astrUD la moNja enAnÃ¡ galacTica lemoNfly Ã lma-X eLlos la CostA bravA manO de santO dinarAma chico y chica..': No such file or directory

It seems that nothing can be done to it because it doesn't exist. However it's there... 

Thanks ardchoille.

---

### Post by xinelo on 2006-08-02
@ardchoille: Reply to your pm:

> Is this a USB device or a device other than your main Ubuntu hard drive?

It is a Iomega USB 160 Gb external hard drive. Do you think that could be related to the problem? 

> If so, and that is the only file on the device, you can always use gparted (or another partition editor) to re-format the device. But, that will get rid of every file/folder on the device.

Unfortunately I have many other files in it, and it wouldn't be easy to move them out to do that. Otherwise it wasn't a bad idea ;) 

> I'll keep trying to think of ways to help you with this until you get it solved 

Thanks ardchoille, that's very kind of you. Let's hope we find a solution! I'll try not to give up :)

Good night, xinelo

---

