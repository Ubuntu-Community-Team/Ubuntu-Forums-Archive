---
title: "Need help with .Pdf file please"
date: 2006-06-14
forum: Desktop Environments
---

### Post by randell6564 on 2006-06-14
Hello!

I have an employment application that I downloaded.  It is in .pdf format.

I dont want to print it and then fill it out.  I would like to fill it out on my computer but I dont know how.  

It will not allow me to add text to it.  Is there a way to add text to a .pdf file?

Or to convert it to another format that will allow me to add text to it?

Thanks!

---

### Post by aysiu on 2006-06-14
Well, does it have a form in it, or does it not?

If it has a form in it, you should be able, with Adobe Acrobat Reader (the *acroread* package), to fill in the information.

Otherwise, you'll have to actually edit the PDF. For that, I'd recommend KWord.

---

### Post by Viskovitz on 2006-06-14
You can fill in pdf forms with Acrobat Reader 7 for Linux. For anything else I prefer evince.

Cheers,
Visko

---

### Post by randell6564 on 2006-06-14
[QUOTE=aysiu]Well, does it have a form in it, or does it not?

If it has a form in it, you should be able, with Adobe Acrobat Reader (the *acroread* package), to fill in the information.

Otherwise, you'll have to actually edit the PDF. For that, I'd recommend KWord.[/QUOTE]

Yes, it Does have a form in it.  But it will not allow me to add text to that form.

So I could copy it to 'Kword' just as it looks in the pdf format?

---

### Post by randell6564 on 2006-06-14
Thank you all!

Im on it!

---

### Post by aysiu on 2006-06-14
Are you using *acroread* or some other PDF reader (like Evince or KPDF)?

Instead of copying to KWord, you would actually use KWord to import the PDF. Then you would export it once you're done (the exports in PDF are counterintuitive--rather than choosing "Export," you pick "Print" and then print to PDF instead of to an actual printer).

---

### Post by randell6564 on 2006-06-14
[QUOTE=aysiu]Are you using *acroread* or some other PDF reader (like Evince or KPDF)?

Instead of copying to KWord, you would actually use KWord to import the PDF. Then you would export it once you're done (the exports in PDF are counterintuitive--rather than choosing "Export," you pick "Print" and then print to PDF instead of to an actual printer).[/QUOTE]

I'm trying to install acroread .tar.gz right now but I'm not sure that i'll be able to do it.

I'm still alittle new to terminal commands!

I'll see what I can do with 'Kword.' Thanks!

---

### Post by aysiu on 2006-06-14
You don't need the .tar.gz to install Acroread. Just [enable extra repositories](http://www.psychocats.net/ubuntu/sources) and then type ```
sudo aptitude update
sudo aptitude install acroread
```

---

### Post by randell6564 on 2006-06-14
[QUOTE=aysiu]You don't need the .tar.gz to install Acroread. Just [enable extra repositories](http://www.psychocats.net/ubuntu/sources) and then type ```
sudo aptitude update
sudo aptitude install acroread
```[/QUOTE]

Yeah, I installed it, I just couldnt remember what to enter after 'apt-get install....'

Anyway, I installed Kword and inporting and exporting worked except when I exported it, it came out kind of funky!

Didnt duplicate the original.  But I'm gettin closer!  Thanks, My friend!

---

### Post by randell6564 on 2006-06-14
Well,

I now have acroread 7 but it still will not allow me to add text to the form.

I've searched in all the menus and cant find anything that pertains to entering text.

---

### Post by aysiu on 2006-06-14
Well, I just tested out filling a PDF form with the *acroread* program, and it works.

So either you aren't using *acroread* (you could be using Evince, for example), or your PDF is **not** a form.

---

### Post by randell6564 on 2006-06-14
[QUOTE=aysiu]Well, I just tested out filling a PDF form with the *acroread* program, and it works.

So either you aren't using *acroread* (you could be using Evince, for example), or your PDF is **not** a form.[/QUOTE]

Well CRAP!

If by form you mean that there is text and images when opening the file with acroread then yes, it is a form.

Its an employment app that was given over the net in acroread pdf format.

I am definately opening it with acroread.  It's installed and located in Applications>office>acroread

What did you do in order to add text to it?  what menu did you go to? how did you set it up?

sorry, Please bare with me!

Hey 'aysiu'!!  I just noticed that it was you!  You seem to always find me and my problems! LOL!

---

### Post by aysiu on 2006-06-14
I just clicked on the line to be filled in and started typing.

Maybe we're having a miscommunication about the word *form*.

A form is generally something that has lines where people are supposed to write stuff. This is probably what you're thinking of when you say *form*. Just because a PDF *looks* like a form doesn't mean it can actually be filled in electronically (i.e., without printing out the PDF and manually filling in the lines with a pen).

The kind of *form* I'm talking about is a special PDF that's designed to be filled in. That is, there are clickable fields within the PDF where people can type data.

You see that yellow bar at the top of my screenshot? It says > You cannot save data typed into this form.
Please print your completed form if you would like a copy for your record If your PDF doesn't have that yellow warning at the top when you open it with *acroread*, it is **not** a form. It's just something that *looks* like a form.

Does that make sense?

---

### Post by randell6564 on 2006-06-14
[QUOTE=aysiu]I just clicked on the line to be filled in and started typing.

Maybe we're having a miscommunication about the word *form*.

A form is generally something that has lines where people are supposed to write stuff. This is probably what you're thinking of when you say *form*. Just because a PDF *looks* like a form doesn't mean it can actually be filled in electronically (i.e., without printing out the PDF and manually filling in the lines with a pen).

The kind of *form* I'm talking about is a special PDF that's designed to be filled in. That is, there are clickable fields within the PDF where people can type data.

You see that yellow bar at the top of my screenshot? It says  If your PDF doesn't have that yellow warning at the top when you open it with *acroread*, it is **not** a form. It's just something that *looks* like a form.

Does that make sense?[/QUOTE]

ABSOLUTELY makes sense!  NOW we are on the same page!

There are no "clickable fields" that allow text input!  (Crap!) :)

So...

Gotta print the Freekin thing out and actually use a pen!  (Crap!)

Thanks 'aysiu'!

---

### Post by aysiu on 2006-06-14
Either that or try to futz with the formatting in KWord and export it as a PDF again afterwards.

---

### Post by randell6564 on 2006-06-14
[QUOTE=aysiu]Either that or try to futz with the formatting in KWord and export it as a PDF again afterwards.[/QUOTE]

Yeah...

Might as well!  It's an oppurtunity to learn!  

Thank You, My Friend!

Hey...!

Congrats on "beanie of the month"!  I'm still Grinding the beans! LOL!

---

### Post by randell6564 on 2006-06-14
Well...

By Playing Around With kWord, I Managed To Fit Everything Where It Was Originally!

But...

That Still Sucks!  LOL!

Until I Can Learn How To CREATE Pdf, I dont Think That I Much Like PDF!

Thanks Again Aysiu!

---

### Post by jeremy on 2006-07-08
To fill in a form using adobe, you need to install
acroread and acroread-plugins

---

### Post by aysiu on 2006-07-08
> **jeremy said:**
> To fill in a form using adobe, you need to install
acroread and acroread-plugins
The issue was filling in the form *and* saving the form information.

Filling in the form and **not** saving it was never an issue.

---

