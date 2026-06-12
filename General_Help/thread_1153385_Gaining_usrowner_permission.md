---
title: "Gaining usr/owner permission"
date: 2009-05-08
forum: General Help
---

### Post by crimlaw on 2009-05-08
I am attempting to copy and paste a theme from my personal folder to usr/share/screenlets/clock, but it tells me that I do not have permission to do this.  How do I gain permission??? I am running 9.04

Thanks!!!

---

### Post by cholericfun on 2009-05-08
as always
sudo mv /path/to/something /somewhere/else

---

### Post by crimlaw on 2009-05-08
Thanks for the quick response.  I am not at all savvy with the terminal.

Would you mind being a little more specific?

should I do something like:

sudo mv /path/to/name_of_file_to_move/usr/share/etc.

---

### Post by cariboo on 2009-05-09
You have a typo in your command there should be a space btween the file name and the path where you are moving the file to.

Your version

```
sudo mv /path/to/name_of_file_to_move/usr/share/etc
```

Correct verison

```
sudo mv /path/to/name_of_file_to_move /usr/share/etc
```

---

### Post by crimlaw on 2009-05-11
ok, tried the command line, and it did not work.  

I typed 

sudo mv /path/to/home/"my folder"/Background/UbuntWood/WoodcairoClock /usr/share/screenlets/Clock/themes

and I received

mv: cannot stat `/path/to/home/"my folder"/Background/UbuntWood/WoodcairoClock': No such file or directory

What did I do wrong???

---

### Post by bodhi.zazen on 2009-05-11
> **crimlaw said:**
> ok, tried the command line, and it did not work.  

I typed 

sudo mv /path/to/home/"my folder"/Background/UbuntWood/WoodcairoClock /usr/share/screenlets/Clock/themes

and I received

mv: cannot stat `/path/to/home/"my folder"/Background/UbuntWood/WoodcairoClock': No such file or directory

What did I do wrong???

Moved to general help.

You need to use the correct path.

~user is short for /home/username , so ..

```
sudo cp -R ~user/my\ folder/Background/UbuntWood/WoodcairoClock /usr/share/screenlets/Clock/themes/
```

Also I suggest you use tab completion to reduce typing and typos

cp ~user/my<tab>

---

### Post by crimlaw on 2009-05-11
Perhaps my lack of knowledge in the terminal is getting in the way

now I tried 

sudo cp -R ~user/"my folder"/Background/UbuntWood/WoodcairoClock /usr/share/screenlets/Clock/themes

and received 

cp: cannot stat `~user/"my folder"/Background/UbuntWood/WoodcairoClock': No such file or directory

and I don't know what you mean by tab completion

---

### Post by mikewhatever on 2009-05-11
Hit alt+f2, type **gksudo nautilus**, enter your password and copy/paste whatever you like graphically.

---

### Post by crimlaw on 2009-05-11
Ha, I got it to work finally in the terminal.  I can't really say what I did.  I screwed around the with command enough, did a little copy and pasting, and the final command line was 

sudo cp -R /home/username/Background/UbuntWood/WoodcairoClock /usr/share/screenlets/Clock/themes/

No idea why it worked this particular time.  I think I kept putting a / after WoodcairoClock.  

Anyway, thanks for everyone who offered advice, I could not have even begun to understand if not for the help.  Maybe next time I will try alt+f2

---

### Post by crimlaw on 2009-05-11
darn, I spoke to soon.  

Now when I double click on WoodcairoClock, just copied to usr/share/screenlets/Clock/themes, it tells me that I do have permission to view the files.  Also, when I go into the preferences of my screenlet clock and click on the Wood theme, the clock disappears. 

Anymore ideas?  I assumed when I copied /WoodcairoClock/ that I would copy its contents, am I wrong?  Also, the /WoodcairoClock/ folding in the /themes/ folder now has a little earth on the upper right-hand corner of the icon, what does that mean?  

Thanks!!!

---

