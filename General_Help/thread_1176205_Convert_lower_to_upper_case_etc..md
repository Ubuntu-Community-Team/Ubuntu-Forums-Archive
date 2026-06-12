---
title: "Convert lower to upper case etc."
date: 2009-06-02
forum: General Help
---

### Post by Ian_M on 2009-06-02
Hello all

What I'm after is a programme/add on/plug in that will allow me to select a section of text and then allow me to format it as upper case/lower case/title caps/sentence caps etc.

I've tried searching for something like this but so far to no avail.

Those of you that are familiar with Mac OS X may know of WordService. An excellent addition to the services menu - one of the more useful apps.

[http://www.versiontracker.com/dyn/moreinfo/macosx/10398](http://www.versiontracker.com/dyn/moreinfo/macosx/10398)

will give you a better description of what I'm looking for.

There *must* be something similar for Ubuntu - isn't there?

Cheers

Ian

---

### Post by Lars Noodén on 2009-06-02
In which program?  

In OpenOffice.org:
Format -> Character -> Font Effects 
(you can make your own keyboard shortcuts)

In Kate:
 to capitalize: ALT-CTRL-u
 for uppercase: CTRL-u
 for lowercase: SHIFT-CTRL-u

In Emacs:
 to capitalize: ESC-c
 for uppercase: ESC-u
 for lowercase: ESC-l

In Vi:
 for uppercase: gUG
 for lowercase: guG

---

### Post by Ian_M on 2009-06-02
> **Lars Noodén said:**
> In which program?  



That's the thing - because WordService is in the services menu it works in all programmes. I mainly use it in Safari or Firefox.

For instance. I sell stuff on eBay. When I'm printing an invoice or packing label the buyer's info is already filled in. Some people don't format names and addresses correctly when they put their details into eBay to begin with.

Using WordService in Mac OS X I can select the name and change it from ian moffatt to Ian Moffatt with one click as opposed to selecting individual letters. Likewise, the old barn linux road becomes The Old Barn Linux Road and so on. It's very useful when I need to capitalise a town name (UK mail system recommends town names to be in uppercase) and might misspell it when going letter by letter.

Postage labels and invoices look more professional if correctly formatted.
It shows that you've taken a bit of care and it's not just a cut and paste job.

IMHO of course ;-)

Cheers!

Ian

---

### Post by MichaelSammels on 2009-06-02
Hey. Try this:

```
sudo apt-get install gprename
```

However, this applies filenames only. I know that's not what are you looking for, but it is rather interesting.

---

### Post by andrew.46 on 2009-06-02
Hi Ian_M,

Some of what you are after can be accomplished with shell scripts, although I suspect you are perhaps after a more 'complete' package? For example some of the following could be incorporated:

```

echo 'transform lowercase to uppercase' | tr [a-z] [A-Z]
echo 'TRANSFORM UPPERCASE TO LOWERCASE' | tr [A-Z] [a-z] 
echo 'Guvf vf ebg13 grkg' | tr [A-Za-z] [N-ZA-Mn-za-m]
echo 'txet eht sesrever sihT' | rev

```

and so on.....

Andrew

---

