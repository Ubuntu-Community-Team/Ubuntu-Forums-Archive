---
title: "how to get &quot;c with cedilla&quot; key?"
date: 2009-05-14
forum: Desktop Environments
---

### Post by alexweber15 on 2009-05-14
I have a standard US keyboard (mapped to generic 105 intl keyboard) and all accents and characters like ãáéê etc work fine but instead of "c with cedilla" (using character map: ç) I get "c acute": &#263;  when pressing: ' + c

this is the only combination that works, can anyone help me please is there a way to remap the '+c behavior to switch from acute to cedilla?

thanks

Alex

---

### Post by Sarai the Geek on 2009-05-14
If you plan on using a lot of accented characters, the best thing you can do is use the international keyboard layout. There's a pretty good explanation of it [here]("http://spanish.about.com/od/writtenspanish/a/dia_ubuntu.htm"), although they're using Spanish as the example it works for most romance languages since you can get all of the main accents (I won't list them because I can't remember how to say most of them in English... ;)) over almost every letter. It takes a little bit of practice to learn but once you've got it down typing in languages with accents goes *much* faster.
You can turn it on in the keyboard layout settings. I recommend you enable both the standard US (UK, CAN, etc) keyboard and the US Alternative International keyboard. You can add an applet to your panel that allows you to switch between them quickly.

---

### Post by jimbog on 2009-05-14
This is the best solution I've found - I often need to write in French.

I have the keyboard layout switcher in my taskbar, and have it set so that a certain key combination (e.g. shift + caps lock) changes between layouts.

It doesn't take too long to learn where the different keys are (in the French layout, the ç key is the 9 key).

---

### Post by alexweber15 on 2009-05-14
Thanks for the replies!

It all seems a bit overkill really... ALL other accents work as expected using my current US-INTL layout, its only really the behavior of combining '+c which outputs accute and I'd like to change to cedilla.

Is there no other workaround short of changing my entire keyboard layout because of 1 key??

Thanks again!

---

### Post by mcduck on 2009-05-14
> **alexweber15 said:**
> I have a standard US keyboard (mapped to generic 105 intl keyboard) and all accents and characters like ãáéê etc work fine but instead of "c with cedilla" (using character map: ç) I get "c acute": &#263;  when pressing: ' + c

this is the only combination that works, can anyone help me please is there a way to remap the '+c behavior to switch from acute to cedilla?

thanks

Alex

have you tried AltGr + ´ + c? I'm not absolutely sure if US-international uses right Alt key as AltGr or not, but it's worth a try..

---

### Post by adrianx on 2009-05-14
It sounds as if you already have "compose key" set up, so try:

Compose Key + , (comma) then c  
That will give you ç

**Edit:**
To set up the compose key (similar to AltGr) on a standard US keyboard, 
System > Preferences > Keyboard. 
Click on the "Layouts" tab.
Click "Layout Options"
Expand "Compose key position" and select a key that you want to use (I use "Right Win")

Here are some [common compose combinations]("http://en.wikipedia.org/wiki/Compose_key").

---

### Post by alexweber15 on 2009-05-14
Hey all thanks for all the replies... I'm still not sure what a compose key is but in testing all your suggestions I figured it out by accident... Right Alt + Comma = ç !!   weird eh?  no pressing of c is required... it's not the most natural combination but will do :)

thanks!

---

### Post by Sarai the Geek on 2009-05-14
I think my favorite part of the intl keyboard is that you can make some crazy characters that aren't, apparently, in unicode. They're readable by other people using Ubuntu but Windows people will complain that they're getting boxes or question marks!
dô ÿõù &#347;êë &#7813;&#293;ã&#7831; ï'&#7743; &#7831;à&#314;&#7729;îñ&#501; äbóû&#7831; ?

I'm real fun at parties... lol.

---

### Post by alexweber15 on 2009-05-14
lol :P

I guess this is the wrong forum to ask anyone with windows if the cedilla shows up properly... ççççç

---

### Post by Sarai the Geek on 2009-05-14
> **alexweber15 said:**
> lol :P

I guess this is the wrong forum to ask anyone with windows if the cedilla shows up properly... ççççç

I could check it with my mac...

---

### Post by djspiegel3 on 2009-10-24
The definitive solution to obtain cedilla/cedilha using ' + c is the following (works for all releases of Ubuntu from 7.10 to 9.10; 7.04 and earlier require different solution):

In terminal type:

sudo gedit /usr/lib/gtk-2.0/2.10.0/immodule-files.d/libgtk2.0-0.immodules

    * Locate the line that reads: 

"cedilla" "Cedilla" "gtk20" "/usr/share/locale" "az:ca:co:fr:gv:oc:pt:sq:tr:wa"

    * At the end of the line insert ":en", as such: 

"cedilla" "Cedilla" "gtk20" "/usr/share/locale" "az:ca:co:fr:gv:oc:pt:sq:tr:wa:en"

Save the file and restart the computer. Cedilla will work as expected.

---

### Post by guriinii on 2009-10-31
> **adrianx said:**
> 
**Edit:**
To set up the compose key (similar to AltGr) on a standard US keyboard, 
System > Preferences > Keyboard. 
Click on the "Layouts" tab.
Click "Layout Options"
Expand "Compose key position" and select a key that you want to use (I use "Right Win")

¡Thank you!

---

### Post by leorolla on 2009-11-19
djspiegel3's solution rocks.

ç instead of acute c

If it doesn't work, I have put a more complete instruction here:
[http://ubuntuforums.org/showthread.php?t=1330912](http://ubuntuforums.org/showthread.php?t=1330912)

---

### Post by pvfloripa on 2010-02-04
Great! Thanks for posting it, djspiegel3.

---

### Post by leorolla on 2010-02-04
> **pvfloripa said:**
> Great! Thanks for posting it, djspiegel3.

Yes, it is really nice!
Thanks djspiegel3

If you want it working for KDE applications, see my post.

And if you think it's **ridiculous** that my grandmother has to edit a text file called "/usr/lib/gtk-2.0/2.10.0/immodule-files.d/libgtk2.0-0.immodules" (what???!!!) to get Ç, so that in the end she stays with other OS's, you may want to vote on [http://brainstorm.ubuntu.com/idea/7603/](http://brainstorm.ubuntu.com/idea/7603/) and hopefully it will work out of the box in the near future.

---

### Post by seff-feedback on 2010-12-16
An easy way is described here:
[https://sites.google.com/site/sefftips/gtk-cedilha](https://sites.google.com/site/sefftips/gtk-cedilha)

---

