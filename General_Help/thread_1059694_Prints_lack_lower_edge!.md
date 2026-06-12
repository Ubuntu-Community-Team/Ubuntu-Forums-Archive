---
title: "Prints lack lower edge!"
date: 2009-02-04
forum: General Help
---

### Post by Takmadeus on 2009-02-04
Greetings.

I hereby notify you of a problem that has plagued me since dapper, but now I cannot stand it anymore.

Whenever I intend to print any kind of document (image, pdf, or a simple text file), even if I configure the printing options properly (set the paper size to US letter), when the result comes out, it always lacks the lower edge of the content (see annexed images for a graphical explanation).

This problem does not happen when I print in windows, or any other linux distro, and it affects ubuntu and kubuntu (have not tried xubuntu).

My printer is a HP Deskjet 3535. I am using ubuntu 8.10 (but as mentioned earlier, it also affects me since dapper)

Has anyone else experienced this problem?, have you solved it? How?

Please, any kind of help is much, much appreciated.

*note: ejemplo 1.png is what I want to print, ejemplo 2.png is what I actually get

---

### Post by cariboo on 2009-02-04
Your images are to small to see what you are complaining about, could you make them full size?

Jim

---

### Post by Takmadeus on 2009-02-04
OK... here is another example....

this is what I want to print

[ATTACH]102216[/ATTACH]

this is what will be missing (the shadowed part is the one missing)

[ATTACH]102217[/ATTACH]

this is what I actually get on paper

[ATTACH]102218[/ATTACH]

---

### Post by Takmadeus on 2009-02-15
OK

found the potential solution for this dreaded problem..

[http://hplipopensource.com/node/232](http://hplipopensource.com/node/232)

Now, I cannot find that /etc/enscript.conf, is it stored somewhere else in ubuntu?

---

### Post by dcstar on 2009-02-15
> **Takmadeus said:**
> OK

found the potential solution for this dreaded problem..

[http://hplipopensource.com/node/232](http://hplipopensource.com/node/232)

Now, I cannot find that /etc/enscript.conf, is it stored somewhere else in ubuntu?

What is in your /etc/papersize file?

---

### Post by Takmadeus on 2009-02-15
it is a4, switched it to letter but I have no results either..., I am going to try and set the printing size to a4 in the preferences, since it looks like it is a specific error when doing letter size

OK, when setting to a4, as the measure is different, I get a smaller print, I have the measures for letter sized paper I got from enscript (which already has the corrected margins for deskjets listed as letterdj)

Here are they

	name		width	height	llx	lly	urx	ury

Media:	Letter		612	792	18	36	594	756
    
Media:  Letterdj        612     792     18      40      594     756

see? those 4 pixels make a lot of difference.


Now the problem is.... how do i tell papersize to set those values?

---

### Post by Takmadeus on 2009-02-15
OK, solved!

Well, as I suspected it is a bug in the hplip drivers, compromising the ppd itself, after some hacking I found the solution.

remember the values I told you last time?, keep them in mind,but just in case I'll post them again...

```

       name    width height  llx  lly urx ury

Media: Letter   612  792     18   36  594 756

Media: Letterdj 612  792     18   40  594 756

```

Remember, there is a difference of 4 pixels between the normal printing of a letter sized paper and the one that should be printed in a deskjet printer.

now, we are going straight to the file that keeps the definitions on where you can print on paper depending on its size (the printer definition or PPD)

```
sudo gedit /etc/cups/ppd/deskjet-3500.ppd
```

(remember, it depends on the ppd of your printer)

now, look for this string (remember to Ctrl + F)

```
*DefaultImageableArea
```

And it will pop up, showing the default paper size for your configuration. Now look a little bit lower and yes, you have found a lot of ImageableArea strings with the very same configurations issued in the list I gave you above.

You might see something like this:

```
*ImageableArea Letter/Letter: "18.00 36.00 594.00 783.00"
```

Yeah, those are exactly the same numbers given above (albeit in a different order)... As expected we just change it to be like this

```
*ImageableArea Letter/Letter: "18.00 40.00 594.00 783.00"
```

Which replaces the 36 (of the default print) to 40 (the ideal for the deskjet printers)

Save the file and print until you explode ;)

---

