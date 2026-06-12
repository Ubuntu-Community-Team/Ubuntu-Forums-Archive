---
title: "Can LyX do multiple languages at once? Can LaTeX for that matter?"
date: 2006-09-26
forum: Education &amp; Science
---

### Post by matthew on 2006-09-26
I'm in the process of writing a book that involves typing things up in Arabic and then giving a translation and explanation in English. I have played around with LyX in an exploratory attempt to decide whether I want to switch to LaTeX instead of writing in OpenOffice. I like the idea of LaTeX and LyX seems to be a nice way to use it. 

I realize that the LaTeX style is generally to use whatever text editor you might like along with accompanying tags for formatting. This appeals to me on some level, but I'm not sure of a method for working with multiple languages at once.

I have downloaded the ArabTex package but in my initial searching it seems that I would have to type in phonetics for Arabic which would then automagically be transformed into Arabic script for me. I would prefer to just type in Arabic and then switch to English within the document. Is this even possible with LaTeX?

Comments?

---

### Post by kleeman on 2006-09-26
Have a look here:

[http://wiki.lyx.org/LyX/LinguistLyX#toc18](http://wiki.lyx.org/LyX/LinguistLyX#toc18)

There is a section on switching languages. I tried it and it looks like Arabic is listed at least. The lyx wiki is a great resource. Also the lyx mailing lists (available through gmane) are very friendly, helpful and knowledgeable.

---

### Post by matthew on 2006-09-26
> **kleeman said:**
> Have a look here:

[http://wiki.lyx.org/LyX/LinguistLyX#toc18](http://wiki.lyx.org/LyX/LinguistLyX#toc18)

There is a section on switching languages. I tried it and it looks like Arabic is listed at least. The lyx wiki is a great resource. Also the lyx mailing lists (available through gmane) are very friendly, helpful and knowledgeable.That is an excellent site. Thank you for the reference. I found this which tells me that for my purposes I may want to continue to use something else for the time being...I'm not talented enough to translate without seeing the arabic text in arabic even if the output would be correct... :) I highlighted the applicable sentence in [COLOR=Red]red.[COLOR=Black] I'll still give it some play-time though in the hopes that with the LyX wiki and some experience I may be able to figure out how to do what I want.[/COLOR][/COLOR]
> **Switching between Languages**

 Switching between, say, English and Greek is easy in LyX. Simply go to [COLOR=darkgreen]Edit&#8594;Text Style&#8594;Language[/COLOR] and select "Greek". This will mark all following text (or the selected text) Greek, unless you switch to another language or chose "reset" to go back to the document's main language (as set in [COLOR=darkgreen]Document&#8594;Settings&#8594;Language[/COLOR]). If you use Aspell as spell checking backend and if the dictionaries are installed, LyX will spellcheck the Greek part as Greek. Foreign languages (i.e. those differing from the document's main language) are marked by a blue underline. 
 [COLOR=Red]Note that inside LyX, only one kind of writing system can be displayed[/COLOR] (i.e. the Roman alphabet if the main language is English, also for the Greek passages). In the output, however, the correct writing systems (Roman alphabet for English, Greek alphabet for Greek) are used. However, LyX 1.5 will use unicode internally, so the situation might improve. 


---

### Post by kleeman on 2006-09-26
Oh I see the issue. Sounds like lyx version 1.5 might help. I believe this is not far off release...

---

### Post by matthew on 2006-09-26
> **kleeman said:**
> Oh I see the issue. Sounds like lyx version 1.5 might help. I believe this is not far off release...I'll watch for it.

---

