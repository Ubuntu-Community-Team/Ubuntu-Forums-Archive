---
title: "Discussion - https://help.ubuntu.com/community/BinaryDriverHowto/AMD"
date: 2016-01-03
forum: Documentation and Community Wiki Discussions
---

### Post by vipri-alessandro on 2016-01-03
Hello everyone,

I'm trying to update the wiki page [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD) for now I have created a sandbox page:

 - [https://wiki.ubuntu.com/vipri-alessandro/AmdBinaryDriverTest](https://wiki.ubuntu.com/vipri-alessandro/AmdBinaryDriverTest)

with all the changes made by me.
I would like to discuss with you about the changes I introduced and, before to copy/paste my sandbox page into the community/BinaryDriverHowto/AMD page, correct  all the errors or inaccuracies you can find in my test page.

So, if you have time please read my sandbox page and tell me what you think or correct it yourself!

Some notes:
 - the wiki style in a sandbox page is different from the wiki style inside the "help.ubuntu.com/community" wiki, so you should not care about this;
 - some links to other wiki pages are for now "broken", but when/if my sandbox page will be copy/pasted inside the "help.ubuntu.com/community" wiki, those links will be correct, so don't take care about broken links for now;
- as you can see, my English is far from perfection, so if you find errors correct them, thanks!

---

### Post by coldraven on 2016-01-03
> However, the proprietary **fglrx** drivers (known as **AMD Catalyst** or **AMD Radeon Software**) are made available for those who would like to use it. The instructions on this page advise on how to install and use **fglrx**.
Maybe either use the singular ===> "fglrx driver..........is made available..................like to use it"
or the plural =================> "fglrx drivers.......are made available..................like to use them"

---

### Post by vipri-alessandro on 2016-01-03
> **coldraven said:**
> Maybe either use the singular ===> "fglrx driver..........is made available..................like to use it"
or the plural =================> "fglrx drivers.......are made available..................like to use them"



 
 
 It was a typo in the original community wiki page (oops).
Feel free to correct errors in my sandbox page without asking :popcorn:

---

### Post by QIII on 2016-01-03
Please do NOT make your changes.  They do not fit the style guidelines.  Yes, we should worry about the style elements in your sandbox.  Get your sandbox in the appropriate style, with the correct style tags.

I see you have taken terminal commands out of the typical grey code boxes.

I also see that you section 4 is missing some important material from the current section 3.1. You have also introduced erroneous data, for instance: indicating that all adapters have to be initialized for multiple x2 cards.  ALL multiple card arrangements must be initialized using -all, even single GPU cards.

Furthermore, thousands of references to wikis have been made on the Forums, with answers specifying particular section headers.  You have made sweeping changes to section headers.  Do you now plan to find all references in solved threads and ask the staff to correct section references?

---

### Post by Bashing-om on 2016-01-03
Never mind ... this response'

QIII is on top of it .

[INDENT][INDENT]anything worth doing
[INDENT][INDENT][INDENT]is worth doing right
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by vipri-alessandro on 2016-01-03
> **QIII said:**
> Please do NOT make your changes.  They do not fit the style guidelines.

For one thing, you have taken terminal commands out of the typical grey code boxes.

[QUOTE=vipri-alessandro]the wiki style in a sandbox page is different from the wiki style  inside the "help.ubuntu.com/community" wiki, so you should not care  about this;[/QUOTE]

If you copy/paste my sandbox page inside the help.ubuntu.com/community wiki and you press "Preview", you will notice that terminal commands are inside the typical grey code boxes. However, I don't want to make any changes before to discuss about what I wrote with you.

---

### Post by QIII on 2016-01-03
What I am saying is that nobody should have to copy and paste your text to check it out.  It is up to you to provide a properly formatted example if you would like it to be discussed.

Second, the newly introduced errors and missing instructions need to be fixed and the previous section structure should be restored.

You may add new sections, but arbitrary changes to the sections will cause a great deal of confusion when someone has found a solved thread pointing to a particular section.

---

### Post by vipri-alessandro on 2016-01-03
> **QIII said:**
> Please do NOT make your changes.  They do not fit the style guidelines.  Yes, we should worry about the style elements in your sandbox.  Get your sandbox in the appropriate style, with the correct style tags.

Do you mean this: [https://help.ubuntu.com/community/Tag#Style_cleanup_required](https://help.ubuntu.com/community/Tag#Style_cleanup_required) ?
I was thinking this is only for *help.ubuntu.com/community* pages, not for sandbox pages. However, I can not change the style of a sandbox page: the syntax I use to write my sandbox page is the same used inside the *help.ubuntu.com/community* original page... I suppose this difference in style is needed to distinguish community wiki pages from personal pages/sandbox pages and blablabla

> **QIII said:**
> I also see that you section 4 is missing some important material from the current section 3.1. You have also introduced erroneous data, for instance: indicating that all adapters have to be initialized for multiple x2 cards.  ALL multiple card arrangements must be initialized using -all, even single GPU cards.

As said before, my sandbox page is far from perfection and I WANT to discuss changes I made before to do everything. That's why I made a sandbox page.

> **QIII said:**
> Furthermore, thousands of references to wikis have been made on the Forums, with answers specifying particular section headers.  You have made sweeping changes to section headers.  Do you now plan to find all references in solved threads and ask the staff to correct section references?

You are right, I was not thinking about this. Let me see if I can change something to make paragraphs according to the original wiki page. However, before or after things can change, you cannot think that a structure of a wiki page must be kept unchanged for years.

> **QIII said:**
> What I am saying is that nobody should have to copy and paste your text to check it out.  It is up to you to provide a properly formatted example if you would like it to be discussed.

How can I do this? The moinmoin syntax I use in my sandbox page is the same of the community wiki pages, are there some settings I have to change to let my sandbox page to look like the community wiki?

---

### Post by QIII on 2016-01-04
Why not simply do as all of the rest of us who contribute to the wikis do instead of replacing the whole cloth:  fix the grammar in place, fix a reference here and there in place, add a more current command  in place when something changes?

Why tear down the building and erect another when all that is needed is for a lightbulb to be replaced?

I applaud your desire to help, but let's not just cut all off the other contributors off at the knees.

Just edit the wiki incrementally and leave a note saying why.  That's how wikis work.

---

### Post by vipri-alessandro on 2016-01-04
Ok, got it! Since the changes I want to add to the wiki are too big, I'll proceed step by step and, if something goes too far from the actual page "structure", I'll ask you before for suggestions. It's not in my mind to replace what you all did or take all the credits, I want only to help and hope this is clear for you.

So, take a look at the edits I'm going to do. If something I change is wrong, correct my edits

---

