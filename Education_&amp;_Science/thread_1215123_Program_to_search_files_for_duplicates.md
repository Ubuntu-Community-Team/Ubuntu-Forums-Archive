---
title: "Program to search files for duplicates"
date: 2009-07-16
forum: Education &amp; Science
---

### Post by Friqenstein on 2009-07-16
Hello all,

First off, yes this was posted in another portion of the forum... in the General Help forum. And I should have known better than to post there because there is so much fodder there that threads get pushed to the 3rd page within 15 minutes... which really is ridiculous. I really don't see how that forum helps anybody at all.

Anyway, please let me explain why I'm here:
I posted here because I know that you guys are always fairly active in your responses and these threads don't move so rapidly as to render them pointless in a matter of minutes.

Now, my question isn't exactly Scientific related, but again, I have found a lot of useful information in this sub-forum in the past, so I trust you guys.

Ok, now that I've rambled enough...

I'm trying to find a program that can search a NAS on a network. I need it to search all the files on the NAS and flag any duplicates so that they can be removed.
Basically think of it this way: NAS has 7GB of movies and you want to find out if anyone has made duplicate copies of movies on the NAS

Simple right? Now I know some will suggest using certain linux commands (rightly so) however this program will need to be used by people of the 'not-so-linux-savvy' nature. So an actual application would be preferred. Even if (gawd forbid) it has to be a winbloz application. I just need to get something setup for some people and make it so idiot proof that... well.. an idiot could use it.

Any help is greatly appreciated. (sorry for the long winded post)

TIA
L8r

---

### Post by PGScooter on 2009-07-17
Hi Friqenstein,

I agree with you about the General Help. I've bumped a thread there 5 times and no response. When you do double post though, I would suggest putting in links in each post to the other. That helps viewers out a lot and can help someone who a week from now searches for something and finds your thread and is looking for an answer. Maybe he will unfortunately fall on the post that doesn't get any hits and for some reason doesn't find the post that has the solution. Here is a link to your general help thread: [http://ubuntuforums.org/showthread.php?t=1215046&highlight=search+duplicates](http://ubuntuforums.org/showthread.php?t=1215046&highlight=search+duplicates)

Now, to your question :)

I've looked at a lot of duplicate file finders in linux. FSlint is a great one. However, I don't know if it can search through NAS. The developer is very responsive to user input and has already implemented several of the features I have suggested. Check it out here: [http://code.google.com/p/fslint/issues/list](http://code.google.com/p/fslint/issues/list)

best of luck!!

---

### Post by norman_ on 2009-07-18
"fdupes" has worked wonders on my photo collection. It matches md5sums I believe.

---

### Post by Friqenstein on 2009-07-18
Thanks for the replies guys.
I didn't post a link to the original thread b'cuz I figured people would waste time (and bandwidth) having to click on the link to see the original question, which alot of people would just not do and go back to the main forum looking to answer a different question.
However you do make a valid point, so thanks for sticking that link in there.

Thanks for the suggestions. I'll give these two a try and see what they do for me. Hopefully they are simple enough that these guys can use them w/out trying to pull out my hair (and I shave my head):P

L8rz

---

### Post by ahmatti on 2009-07-19
> **Friqenstein said:**
> 
Now I know some will suggest using certain linux commands (rightly so) however this program will need to be used by people of the 'not-so-linux-savvy' nature. So an actual application would be preferred.

I'm not going to suggest a command, but make a comment.. I find that many times the easiest way to find a good GUI app that performs a simple task for the less savvy users is to make on yourself...

Often what you need for a task is just a few shell commands or a small perl or python script etc. If this is the case then you can very easily make a GUI for the needed scripts e.g with kommander or python. What I usually need to do is to put in a few options and a big red start and maybe abort buttons.

A good tutorial that gets you started with python GUIs is [http://zetcode.com/wxpython](http://zetcode.com/wxpython), the same site also has tutorials for PyGTK and pyQT, choose the one you prefer.

I know this is not exactly what you asked for, but since this is the education section for the forum I couldn't help offering my views ;)

---

