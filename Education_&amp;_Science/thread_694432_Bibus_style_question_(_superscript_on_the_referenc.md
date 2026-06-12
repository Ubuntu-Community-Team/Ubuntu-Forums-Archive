---
title: "Bibus style question ( superscript on the references)?"
date: 2008-02-12
forum: Education &amp; Science
---

### Post by maxguan on 2008-02-12
Hey everyone:

I am currently using bibus as my primary bibliographic management. Everything work very well. However, I am having a difficulty with some reference style.

We know that if we try to create a new style in bibus, the 1st box in the reference is "identifier", which allows us to match the number of each bibliographic citation then organize in the last page of our paper.

Some of the journals have a special way to represent the references, it is not just like [1]. or 1 . 
they required a superscript, below is an example : 

[img]http://lh3.google.com/maxguan7/R7I3XdqXcuI/AAAAAAAAACU/j9CN93WrM18/iden.JPG[/img]

Is there any way to make the "identifier" as a superscript like in the picture?? or how should I change the code of the style file? instead of manually editing the superscript use openoffice endnote feature.


Thank you

---

### Post by machoo02 on 2008-02-12
Hi,

Open up the style editor (you can either make a new one, or edit an old style file), and click on the "Citation" tab.  At the very top there is a box labeled 'Position'; this determines the location of the citation relative to your text.  Select 'Superscript', and you should be all set.

---

### Post by maxguan on 2008-02-12
> **machoo02 said:**
> Hi,

Open up the style editor (you can either make a new one, or edit an old style file), and click on the "Citation" tab.  At the very top there is a box labeled 'Position'; this determines the location of the citation relative to your text.  Select 'Superscript', and you should be all set.


I tried this before, the "superscript" in the "citation tap" is only work for the number you cited, such as I write a sentence and after that sentence I cite a reference, and the citation number after that sentence would become superscript. However, the list of references at the end of page would not become superscript numbers in the pic above. 

How should I implement this?

---

### Post by machoo02 on 2008-02-12
I'm not sure since I don't think you were able to attach the picture correctly in your original post.  Pleast try to post it again so I can see what you mean.  Alternatively, can you give me an example of a journal that formats citations in this way?

---

### Post by maxguan on 2008-02-12
> **machoo02 said:**
> I'm not sure since I don't think you were able to attach the picture correctly in your original post.  Pleast try to post it again so I can see what you mean.  Alternatively, can you give me an example of a journal that formats citations in this way?

Thanks for replying, machoo02

Sure the picture link is [http://lh3.google.com/maxguan7/R7I3XdqXcuI/AAAAAAAAACU/j9CN93WrM18/iden.JPG](http://lh3.google.com/maxguan7/R7I3XdqXcuI/AAAAAAAAACU/j9CN93WrM18/iden.JPG) or this [http://picasaweb.google.com/maxguan7/Space/photo#5166252598786224866](http://picasaweb.google.com/maxguan7/Space/photo#5166252598786224866)

Journals like "Journal of Applied Physics", "Applied Aphysics Letters"

---

### Post by tweedledee on 2008-02-13
> **maxguan said:**
> Hey everyone:

I am currently using bibus as my primary bibliographic management. Everything work very well. However, I am having a difficulty with some reference style.

We know that if we try to create a new style in bibus, the 1st box in the reference is "identifier", which allows us to match the number of each bibliographic citation then organize in the last page of our paper.

Some of the journals have a special way to represent the references, it is not just like [1]. or 1 . 
they required a superscript, below is an example : 

Is there any way to make the "identifier" as a superscript like in the picture?? or how should I change the code of the style file? instead of manually editing the superscript use openoffice endnote feature.
Thank you

Since the bibliography ends up as a single style, I don't believe you can do this directly.  There may be a way to hack the bibus python code to add multiple styles, but I'm not sure OO allows that within fields.  If you are interested in pursuing this option, your best bet is the Bibus forums or bug/freature tracker on Sourceforge.

However, I can suggest a workaround that might be okay.  If you leave off the identifier (number) from the style in Bibus, but leave the rest unchanged, you'll have everything but the number.  After you finalize, you can then add numbering to the references, and use a character style for the numbers that is superscript.  You'll also need to modify the tabs, etc. in the numbering setup so that everything appears correctly.  Since Bibus will still sort them by number, everything should work out the same.  Once you set up the styles, it's just a matter of applying the numbering after finalizing, which is a lot less work than manually changing each number.

---

### Post by machoo02 on 2008-02-13
Well, after looking around at all of the options in the style editor and in the bibus code, it doesn't seem that this is an available option in the current release.  You might want to head over to the [Bibus project site]("http://sourceforge.net/projects/bibus-biblio/") and suggest this to the developer.  It seems like this would be an easy addition (as there is already an option to format the in-text citation this way).

Another workaround that would be easier than what tweedledee suggested would be to use the number as the identifier in the bibliography, and when after you have finalized the document, simply make all of those numbers superscript.

Here's a style file to get you started.  I only formatted the journal article reference type as I'm not familiar with the physics journals (I'm a biologist myself)

---

### Post by maxguan on 2008-02-13
Thanks for helping.  I will report this issue to the bibus developers.

machoo02, I know how to do tweedledee's suggestion.  But you say that we can use the number as the identifier and finalize it, then, how can I make all of those numbers superscripted in openoffice? it seems impossible to me just superscript the identifer after you finalized the document...

---

### Post by machoo02 on 2008-02-14
After the document has been finalized, the inserted citations are just simply text.  You can edit the text to you heart's content after finalization.  All you need to do is highlight the identifier in your references section and make them superscript manually.  The only difference between the suggestion's from tweedledee and me is that in the former you have to type in the reference number yourself, and in the latter Bibus is doing it for you and you are just changing the format to superscript.  Highlight the identifier, then select Format->Character, and on the 'Position' tab choose superscript.

---

### Post by vanadium on 2008-02-20
There is a convenient, automated way in which you can realize this: this is one particular area where the build-in bibliographic function complements bibus.

Just create your bibliography with numbers as usual.  go to the reference list, right-click - edit. On the "entries" tab, select the "Sh" button, which is the placeholder for the number in the template of the reference. Next to the character style, click the "edit" button: on the position tab, you can select Superscript.

This is the extremely powerful style mechanism of OOo in action.

---

### Post by machoo02 on 2008-02-20
Vanadium,

That almost works...when I tried that, it turned all of the text (and not just the reference number selected by 'Sh') into superscript.

---

### Post by vanadium on 2008-02-23
Strange because for me it worked as expected. Are you sure you changed the correct character style? Maybe you should apply a different character style manually? For it to work, the character style of the SH field obviously must be a different one than that used by the other bibliography elements.

---

### Post by machoo02 on 2008-02-23
Yeah...that does it.  I didn't change the character style for 'Sh', and it applied the superscript to all of the reference text that had the same character style as 'Sh'.  Thanks for the cool tip!

---

