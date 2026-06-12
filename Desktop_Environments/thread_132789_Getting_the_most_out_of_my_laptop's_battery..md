---
title: "Getting the most out of my laptop's battery."
date: 2006-02-19
forum: Desktop Environments
---

### Post by Ricapar on 2006-02-19
I have an Acer Aspire 5002 WMLi which I've had running Linux since the day I got it. I've had a few problems with it, such as the wireless not working, and getting no readout on the battery status. Right now though, everything is working fine!

The only thing that I'm not really happy with is the laptop's battery life. On avarage, I get around a little more than two hours off of it. It has nothing to do with Linux, as I actually get a little bit more on Linux than I do on Windows. 

I'm wondering if there are any other things I could do to squeeze a bit more life out of my battery. My CPU (AMD Turion 64) supports frequencey scaling, it switches between 800MHz and 1.6GHz. Of course, it'll use less power while it's at 800Mhz. Is there any way to keep it locked at 800MHz? I already have the frequencey moniotr applet set to allow the changing of it, but it'll up itself back to 1.6GHz every now and then for a while. I'm willing to sacrifice a bit of performance for some more battery.

Any idea how to keep the CPU frequencey locked at 800MHz? Any other tips that might be helpful?

---

### Post by cilynx on 2006-02-19
Edit (or create) /etc/defaults/powernowd

Update (or add) the line

```

OPTIONS="-q -m 2"

```

The "-m 2" puts powernowd in "passive" mode.  Basically, it's battery conservation mode as opposed to "1" which is "aggressive".

Edit:

That should be "/etc/default/powernowd".  No 's' on "default".

---

### Post by Ricapar on 2006-02-19
That seems to have done something, but at points it keeps jumping back up to 1.6GHz if I add a bit of load. Would there be a way to set it to a manual mode, where I, and only I decide at what speeds it runs at?

---

### Post by nanotube on 2006-02-19
more battery saving tips:
- turn the brightness of your monitor all the way down
- turn off sound if not using it
- turn off wireless if not using it

and seriously, if your cpu only blips up occasionally to 1.6, it probably does not make any appreciable impact on battery life.

---

### Post by bubbadawg on 2006-02-19
[QUOTE=cilynx]Edit (or create) /etc/defaults/powernowd

Update (or add) the line

```

OPTIONS="-q -m 2"

```

The "-m 2" puts powernowd in "passive" mode.  Basically, it's battery conservation mode as opposed to "1" which is "aggressive".[/QUOTE]

I found this thread thru the search and am attempting to follow your directions. I don't seem to have a folder named "defaults" in the etc dir. I have a "default' dir ~ is this the one  you are referencing? If so, I don't see a powernowd file? How would I create this file. 

Thanks - I am new to Ubuntu only using it for less than a week.

---

### Post by nanotube on 2006-02-19
yes, that is /etc/default
and yes, powernowd does not exist there by default. to create it, just start editing a blank text file, and add that line to it, and then save it to /etc/default.
(dont forget to do it with sudo. more info about sudo is here [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo))

---

### Post by bubbadawg on 2006-02-19
[QUOTE=nanotube]yes, that is /etc/default
and yes, powernowd does not exist there by default. to create it, just start editing a blank text file, and add that line to it, and then save it to /etc/default.
(dont forget to do it with sudo. more info about sudo is here [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo))[/QUOTE]

Ok, thanks for kind assitance. Not to sound like a total (helpless) newbie :confused: , but can I create the text file using OpenOffice? If I need to use terminal, what is the command to create/save a text file.

Thanks for the continued help.

---

### Post by bubbadawg on 2006-02-19
Ok. I created a text file in my home directory and then using Terminal moved it to the etc/default directory. Is this the only way to do it? 

Thanks for the help.

---

### Post by nanotube on 2006-02-19
well, openoffice is not really the best for making plain text files. use gedit for that, or the terminal. 

the way you did it is just fine. but if you wanted to avoid the "moving" bit, you could just issue command
```
sudo nano /etc/default/powernowd
```
paste in that line, then upon exit it will ask you if you would like to save it, and say yes... (nano is a friendly editor for the terminal). 

in general, you might want to search these forums for a thread about command line tutorial, there was a nice link to a good tutorial somewhere here...

---

### Post by bubbadawg on 2006-02-19
[QUOTE=nanotube]well, openoffice is not really the best for making plain text files. use gedit for that, or the terminal. 

the way you did it is just fine. but if you wanted to avoid the "moving" bit, you could just issue command
```
sudo nano /etc/default/powernowd
```
paste in that line, then upon exit it will ask you if you would like to save it, and say yes... (nano is a friendly editor for the terminal). ........
[/QUOTE]

Thanks. I tried that out as well using both nano and gedit. Originally I had saved the file, 'powernowd.txt'. But, after reading your post, I am guessing that I don't need the '.txt' extension?

Thanks.

---

### Post by nanotube on 2006-02-19
correct, no need for .txt extension. :)

---

### Post by bubbadawg on 2006-02-19
[QUOTE=nanotube]correct, no need for .txt extension. :)[/QUOTE]
Great. Thanks very much for all of your assistance!

---

### Post by nanotube on 2006-02-20
have fun! :)

---

