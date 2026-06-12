---
title: "Custom Application Launcher"
date: 2006-01-19
forum: Desktop Environments
---

### Post by Bloke on 2006-01-19
I want to add a launcher pointing to my Eternal Lands .bin file. 

My install directory is " /home/ubuntu/el ", and the file is: " el.x86.linux.bin ".

What do I type in the "Command:" field within the Custom Application Launcher setup window?

---

### Post by aysiu on 2006-01-19
Have you tried ```
/home/ubuntu/el/el.x86.linux.bin
```?

---

### Post by Bloke on 2006-01-19
[QUOTE=aysiu]Have you tried ```
/home/ubuntu/el/el.x86.linux.bin
```?[/QUOTE]

Yes I have. That doesnt work.

---

### Post by Sutekh on 2006-01-19
Well as far as I know, .bin files are executed by
```
./name_of_file.bin
```
or
```
sh name_of_file.bin
```
when in the containing directory

So try
```
chmod +x /home/ubuntu/el/el.x86.linux.bin
```
to ensure that the file is executable.

Then
```
./home/ubuntu/el/el.x86.linux.bin
```
or
```
sh /home/ubuntu/el/el.x86.linux.bin
```
in the command box

---

### Post by Bloke on 2006-01-19
Thank you for replying Sutekh, but none of those things worked.

---

### Post by aysiu on 2006-01-19
According to the Eternal Lands website... > **To play in Linux:**
download the zip file, and unzip it cd to the directory where you isntalled it chmod to 775 and execute el.x86.linux.bin
Also, the zip file has no base directory, so you should unzip it in a new directory you create.  So I would do ```
cd /home/ubuntu/el
sudo chmod 775 el.x86.linux.bin
``` and then ```
./el.x86.linux.bin
``` Or just double-click on the file *el.x86.linux.bin*.

---

### Post by Bloke on 2006-01-19
aysiu : I know what el site says, and I have done those things, but thats not what I want to do. I want to create a Launcher on the Panel in Gnome.

---

### Post by aysiu on 2006-01-20
[QUOTE=Bloke]aysiu : I know what el site says, and I have done those things, but thats not what I want to do. I want to create a Launcher on the Panel in Gnome.[/QUOTE] Weird, but I don't think it *can* be a launcher. I downloaded it, tried it out myself. I even dragged it to the panel. I tried moving it to the /usr path.

There's no go on it being a launcher, as far as I can tell. You have to double-click it (and not a link to it, either) to get it started.

---

### Post by Bloke on 2006-01-20
anyone else have an idea?

---

### Post by cogsprocket on 2006-10-26
```
sh -c "cd /home/ubuntu/el && ./el.x86.linux.bin"
```

I don't know how I came across this, but that should work.

---

### Post by Bloke on 2007-02-06
> **cogsprocket said:**
> ```
sh -c "cd /home/ubuntu/el && ./el.x86.linux.bin"
```

I don't know how I came across this, but that should work.

that did work ... thanks!

---

