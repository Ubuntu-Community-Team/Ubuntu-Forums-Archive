---
title: "Help,cant read the characters æøå on webpages"
date: 2009-02-22
forum: General Help
---

### Post by dadman on 2009-02-22
Hi community!  [SIZE="1"]won't excuse my english, but it could be better ;)[/SIZE]

Newbee as i am to this platform, i've come across a problem that i can't figure out. 
I'm trying to create a webpage, and living in Denmark, 
i'm using some characters that only used here in this country, æ ø å, similar to ,ae,oe,aa,. 
When i'm typing, using Gedit there seems to be no problem, but when I upload the file 
and whatch it in Firefox (or ms. explorer), 
all the æ ø å's are replaced whith question marks, 
i have tried to change the charset from "utf-8" too "ISO-8859-1" and "ISO-8859-15", but that didn't bring me anywhere.

The same problem came up, when i installed FreeWebshop.org on my site, with the Danish template.

I have being messing around with this problem for days now (not to mention the other problems i have had with my new Os ;)). 
The only solution i have found is to go to menu "VIEW-character encoding-iso-8859-15", 
but then when i go to another page the ?-marks are back. 
Any other webpages i have seen from Denmark have the right character encoding displayed, looking at the source from those pages, 
don't tell me the differences..... 

Have anyone out there a explanation, or the solution for my problem, 
i'm stucked, so PLEASE let me know.

Kind regards DADMAN  [SIZE="1"]"newbee at 52 ;)"[/SIZE]

---

### Post by mcduck on 2009-02-22
Are you defining the character set in the header section of your web page? You need to do that, an use same character in your text editor and in the web page's header.

(any of the character sets, utf8, ISO-8859-1 and ISO-8839-15 should work for you, as long as the character set used when creating the file and character set defined in the file's header are same.)

In some cases this kind of problems can occur if the web server itself is sending information about character set used and that's not same as what you are actually using, but this is pretty rare and usually related to database-powered sites.

edit: Of course there'a also the fool-proof way of using HTML entities instead of typing the special characters as they are. This should work *always*, regardless of any character set definitions.

å = &aring;
Å = &Aring;
æ = &aelig;
Æ = &AElig;
ø = &oslash;
Ø = &Oslash;

edit2: here's a list of HTML entities for ISO-8859-1: [http://www.w3schools.com/tags/ref_entities.asp]("http://www.w3schools.com/tags/ref_entities.asp")

---

### Post by dadman on 2009-02-22
Thanks for your quick response!
i have defined the charset to iso-5589-1, and it is the same in other browsers, on other OS's to, thinking about your answer with the HTML entities, i wonder if it is the editor that, even writhing the right on my screen, they don't put out the right code, if i have to use the entities it will be a lot of writhing, so maybe the way around it, is to find another editor that gives the right character encoding, or if i can change that parameter in the editor, i have just downloadet SCREEM and that put out the same problem. 
I must admit that i am a bit confused and in doubt of what i should do, because it is limiting the ease of using the software.

If you would like to have a look at my problem, i have put a simple text page on my site at [www.govertz.dk]("http://www.govertz.dk").
Kindly regards
Dadman   [SIZE="1"]Newbee at 52 ;)[/SIZE]

---

### Post by mcduck on 2009-02-23
> **dadman said:**
> Thanks for your quick response!
i have defined the charset to iso-5589-1, and it is the same in other browsers, on other OS's to, thinking about your answer with the HTML entities, i wonder if it is the editor that, even writhing the right on my screen, they don't put out the right code, if i have to use the entities it will be a lot of writhing, so maybe the way around it, is to find another editor that gives the right character encoding, or if i can change that parameter in the editor, i have just downloadet SCREEM and that put out the same problem. 
I must admit that i am a bit confused and in doubt of what i should do, because it is limiting the ease of using the software.

If you would like to have a look at my problem, i have put a simple text page on my site at [www.govertz.dk]("http://www.govertz.dk").
Kindly regards
Dadman   [SIZE="1"]Newbee at 52 ;)[/SIZE]

Gedit uses your system character set by default (usually utf-8), but you can select any charset you want when opening or saving the file.

It definitely works fine for web coding, that's how I earn my living and coming from Finland, I need a couple of funny letters every now and then as well.. ;)

---

### Post by mcduck on 2009-02-23
I took a look at your page, and when I view the source code it defines the character set as "iso-8859-1", but when I check the encoding from the document itself it seems to be UTF-8..

If you use Gedit, I recommend using UTF-8 for encoding, and then defining that in your page as well.

I opened you page in Gedit, made sure all characters are correct (as far as that's possible with my danish skills :D) and saved it as UTF-8, with character set UTF-8 defined in the header. Seems to work fine, at least when tested on my server. I attached the file (zipped) for you.

I also took the time to edit into standards-compliant XHTML and included that as well, and included that in the archive as well in case you are interested.. ;)

---

### Post by dadman on 2009-02-23
**Thanks,** you solved my problem, i was not aware of the character encoding option, at the bottom. I reloaded the script, and then saved it out in utf-8, as you did, and there it was. Thanks again, it was becoming a headache turner for me. (thanks for the work on my file ;)) 

And thanks to those who tried to help me, i must say this community **works!**

So i can gladly say that my problem is **_SOLVED!_**

Now i will try to find the right files in FreeWebShop and load/save them out the right way, it is not files i've made, so i am not the only one, not aware of this conflict between charset enoding.

Kindly regards

Dadman   [SIZE="1"]newbee at 52 ;)[/SIZE]

---

