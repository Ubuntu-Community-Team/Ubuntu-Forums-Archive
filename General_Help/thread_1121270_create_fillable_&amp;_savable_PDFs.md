---
title: "create fillable &amp; savable PDFs?"
date: 2009-04-09
forum: General Help
---

### Post by grashdur on 2009-04-09
With OpenOffice I can create a form, and then export it to PDF format. The resulting PDF file *can be filled in* using the Adobe Reader in Ubuntu or another operating system -- BUT any information a user fills in cannot be saved in the file. 

Is there any way to create a fillable PDF form that's also *savable*? (for example, like the IRS' PDF tax forms are savable) I've tried installing Scribus, but it's more time-consuming and gives lower-quality output than OpenOffice, and still can't create a *savable* form.

Looking around online, it appears that no program anywhere can make a savable PDF form, other than Adobe's own programs that cost hundreds of dollars, and aren't available for Ubuntu Linux anyway. Anyone?

Or is there another way? I've tried "protecting sheets" in OpenOffice, which might also be possible when saving to .xls format, but OpenOffice refuses to protect the sheet, due to some program glitch.

(The purpose of this: My wife is starting a little gardening business, and wants to email a little checklist to clients, so they can check off the plants and options they're interested in. We don't expect her clients to be savvy enough to know how to "print to PDF to create an image of the form to email back.")

---

### Post by hyper_ch on 2009-04-10
I used this:  [http://www.cabaret-solutions.com/en/downloads/linux](http://www.cabaret-solutions.com/en/downloads/linux)

You need to download from the German page as the English one produces an error. However I noticed that it won't work (out of the box) in Jaunty (I need to check my java settings)

---

### Post by ricardisimo on 2009-04-10
Can you point me to a basic tutorial on creating fillable PDFs? I'm not that concerned about the saving part, just being able to create the damned things. Every link I found the last time I looked pointed to some Dutch woman's tutorial, but her blog was long gone by the time I checked. Thanks in advance.

---

### Post by ricardisimo on 2009-04-10
Huh? Please don't tell me that bots have taken over UbuntuForums! Is there a way to report this crap?

---

### Post by mazato on 2009-04-10
have a look here!
[http://www.oooforum.org/forum/viewtopic.phtml?t=60028](http://www.oooforum.org/forum/viewtopic.phtml?t=60028)
I created a form in OO and then exported it. then i opened it with Foxit Reader, then saved it with the entered info.
It works!

---

### Post by mazato on 2009-04-10
The only thingy is that they might have to install Foxit Reader
[http://www.foxitsoftware.com/pdf/reader/]("http://www.foxitsoftware.com/pdf/reader/")

---

### Post by ricardisimo on 2009-04-10
Saving the info aside, how does one create the actual "fillable" part?

---

### Post by mazato on 2009-04-10
You would have to go to the View menu, then toolbars, and check Forms Control.
You will have its toolbar somewhere.

---

### Post by grashdur on 2009-04-10
2 hyper_ch: That Cabaret program looks pretty cool. Unfortunately I was not able to install it in Ubuntu. 

2 mazato: Foxit Reader might be a partial solution, though there's no version for Macintosh. I'll have to give it a try in Windows.

2 ricardisimo: It's pretty easy, so you won't really need a tutorial: You start by creating a form in (any of the programs in) OpenOffice. As Mazato was saying, you click View > Toolbars > Form Controls. This opens a special toolbar that will give you the necessary options for creating a form. Once you have your form ready in OO, click File > Export as PDF... (You can also export with the PDF icon on the main toolbar, though that doesn't show you all the non-default options.) Then you have your fillable (non-savable) PDF! So far I think that OO is by far the easiest way to create a fillable PDF form.

---

### Post by ricardisimo on 2009-04-12
I'm remembering one of the problems that I had with this before, namely that mousing over button in OOo doesn't give any text so as to clue you into what you're doing ahead of time (evidently a well-reported bug in either OpenOffice, or nvidia, or something else.) Although the icons do give good hints, the Form Controls are not as simple without some descriptive text.

Thank you very much for the tip, however. It's exactly what I needed to get started. Wish me luck.

---

### Post by cocamoxb on 2010-07-09
I don't suppose, over a year later, that this post will get much attention, but has there been a development in creating a fillable and savable PDF in Ubuntu, or Linux, for that matter?

---

### Post by mike555 on 2010-07-09
Have you tried Xournal ? not sure about letting others fill in but you can on Ubuntu..

---

