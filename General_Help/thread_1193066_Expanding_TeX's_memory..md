---
title: "Expanding TeX's memory."
date: 2009-06-21
forum: General Help
---

### Post by Timtro on 2009-06-21
Hi All,

No reply needed here. I just went through a small pain in the butt. There's not much information out there about PROPERLY expanding TeX's memory.

This is an increasing issue with many of the more graphically rich packages requiring more memory. ConTeXt springs to mind as another memory hog.

My specific run in was with my thesis and some plots I made with the lua based TikZ terminal in GNUPLOT. These plots quickly ate up TeX's memory, leaving with errors like
```

Runaway text?
! TeX capacity exceeded, sorry [main memory size=...].
...
If you really absolutely need more capacity,
you can ask a wizard to enlarge me.

```
but doesn't tell us who these wizards are.

What's worse is that there is some bad advice floating around the Internet about the proper way to do it. I thought I would write up this quick little gem.

Start by going to /etc/texmf/texmf.d. These are where the files are that you should edit. Not texmf.cnf, which is the advice floating around. I grepped to find where main_memory was set:
```
gksu gvim 95NonPath.cnf
```
Obviously, you don't need to use vim. Search for main_memory, and set it as high as you need it (I set it to 5500000, just to be safe):
```

% If you want to change some of these sizes only for a certain TeX
% variant, the usual dot notation works, e.g.,
% main_memory.hugetex = 20000000
% 
% If a change here appears to be ignored, try redumping the format file
% with fmtutil-sys.

% Memory. Must be less than 8,000,000 total.
% 
% main_memory is relevant only to initex, extra_mem_* only to non-ini.
% Thus, have to redump the .fmt file after changing main_memory; to add
% to existing fmt files, increase extra_mem_*.  (To get an idea of how
% much, try \tracingstats=2 in your TeX source file;
% web2c/tests/memtest.tex might also be interesting.)
% 
% To increase space for boxes (as might be needed by, e.g., PiCTeX),
% increase extra_mem_bot.
% 
% For some xy-pic samples, you may need as much as 700000 words of memory.
% For the vast majority of documents, 60000 or less will do.
% 
main_memory = 5500000 % words of inimemory available; also applies to inimf&mp
extra_mem_top = 0     % extra high memory for chars, tokens, etc.
extra_mem_bot = 0     % extra low memory for boxes, glue, breakpoints, etc.
.
.
.

```
Note the warning that you can't go above 8E6.

Now that that's done, you need to rebuild you config files
```
sudo update-texmf
```
And at this point, I think you're done. Try it and see if you get the memory nag. If you do, then
```
sudo update-fmtutil
```
to redump the .fmt file, but I don't think I had to do this.

---

### Post by newagelink on 2009-07-21
I am having a similar problem, but it seems I must edit the file a little differently; please help!

As far as I can tell, the standard values: ```
main_memory = 1500000 % words of inimemory available; also applies to inimf&mp
stack_size = 5000	% simultaneous input sources
``` result in the following error: > Errors:
TeX capacity exceeded, sorry [input stack size=5000]
Description:
\lyxframeend
          {}\subsection{Previous Work}
If you really absolutely need more capacity, you can ask a wizard to enlarge me. while the edited values: ```
stack_size = 10000	% simultaneous input sources
``` yield instead > Errors:
TeX capacity exceeded, sorry [input stack size=6000].
Description:
\lyxframeend
          {}\subsection{Previous Work}
If you really absolutely need more capacity, you can ask a wizard to enlarge me.
I have tried editing param_size and main_memory along with stack_size. What values do I need where? I've read through all of Part 3 of 95NonPath.cnf and I don't know what to do. :(

---

### Post by Timtro on 2009-08-21
I'm sorry, I really don't know much about it. Perhaps this post will bump it back up for you for someone else to look at.

---

### Post by bakom on 2009-08-30
Hello,

I did as you posted, but It seems, that nothing has changed, because I still get the same error:

> 
Runaway argument?
{\expandafter \XC@calc@ \@@clr ,,,,:N\let \@@clr 
! TeX capacity exceeded, sorry [main memory size=1500000].
<argument> ...lc@ \@@clr ,,,,:N\let \@@clr \@@tmp 
                                                  
l.41132 	cycle;
               
!  ==> Fatal error occurred, no output PDF file produced!
Transcript written on Bericht.log.


Any hints?

---

### Post by berland on 2009-09-08
What can be done when you do not have root access, besides installing a tex distribution on your home directory (which I assume would be quite much work)?

---

