---
title: "Slow Nautilus: Klick... Wait... Klick ... Wait..."
date: 2009-05-12
forum: Desktop Environments
---

### Post by bbruecker on 2009-05-12
Since I updated 9.04 Nautilus makes me angry.

It eats CPU-Time. Every time I browse a folder with some more subdirectories or a different partition nautilus assumes 80-90 percent of CPU. Why? What's going on?

Examples:

[LIST]
[*]Pressing Ctrl+L: 5 to 8 seconds
[*]Pressing Ctrl+T for a new tab 10 seconds
[*]changing from symbol to list view: to 10 seconds
[*]Displaying Content of my data-partition: 12 seconds
[*]closing that proggy: 5 to 15 seconds, sometimes there is an warning: "File-Browser is not responding"
[/LIST]
I'm not amused. It seems after update only boot process is faster.

Nothing of that helped:

[LIST]
[*]questioning my logs: no errors reported
[*]disabling previews
[*]deleting content of .nautilus and .thumbnails folders
[*]activate nvidea or deactivate nvidea binary graphic
[*]activate or deactivate compiz
[*]checking hardisk-performance:```
Timing cached reads:   720 MB in  2.00 seconds = 359.83 MB/sec
Timing buffered disk reads:  138 MB in  3.02 seconds =  45.64 MB/sec
```
Isn't that bad for a pata-disk.
[/LIST]
PCMan Filemanager displays the content of the same folders quickly. (But I have some other issues with that proggy.) 

Strange: My slower netbook computer is faster doing same operations with 9.04.

Any further ideas?

Benjamin

---

### Post by jbtito03 on 2009-05-17
Hi

Did you upgrade from 8.10 or did you do a clean install? 

Could you paste the nautilus debug output or logfile?

Cheers,

J.B.

---

### Post by Jammy4041 on 2009-05-17
PCManFM served me well when I was using LXDE. Have you ever considered using a lighter Window Manager e.g. XFCE, LXDE etc? 

You might want to also consider purging any extensions that you might have and in a worst case scenario, reinstalling nautilus/gnome/ubuntu

---

### Post by bbruecker on 2009-05-17
Thank you both for answering my post. 

@ jbtito03,

I've done a clean install. Where can I find the debug output? When I call nautilus from prompt there is no output displayed. Where can I find the logfile for nautilus?

Hello Jammy4041,

yes I was thinking about xfce which is a realy faster desktop. I've tried it with prior versions of ubuntu but my result was it is not necessary, because gnome is fast enough. After installing 9.10 some operations are much more faster, e.g. booting, editing films with avidemux (this is dramtically faster 30%), copying files over network (not much, but 5 percent). But nautils makes me angry. 

I've not installed any extensions or plugins to nautils. In the end, I've installed ubuntu again (that strategy of trouble-shooting makes me remember on MS-Windows-trouble; I'm not very happy). Before I worked with nautilus I've disabeld any previews, and I think it is working a little bit faster. But not dramtically.

What I can see is again this: when I start nautilus or when I change to a partition or a folder with more than 5 subfolders nautils takes 80 to 90 percent of processor for 5 seconds. Nautils is calculation something. But what? I've disabled any preview, including the number of subfolders. It can't be so difficult in displaying 7 foldes from my data partion? What is this program doing?

Because my netbook computer doing the same jobs much more faster, I think this behavior is an indicator to some other issues. Maybe it is a nvidea card. Ot the fact that the computer has two network adapters or something like that. 

Any Ideas?

Regards, Benjamin

---

### Post by jbtito03 on 2009-05-31
Okey..

I think the best thing is, that you go into the folder /home/username/.nautilus/ and delete all the files as also in the subfolder /metafiles/ and then try to open a folder.

It worked for me :)

Cheers..

J.B.

---

### Post by kingaaronj on 2009-06-02
Try removing the tracker package.

```
sudo apt-get remove tracker --purge
```

---

