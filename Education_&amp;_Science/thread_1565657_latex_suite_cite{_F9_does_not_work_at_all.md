---
title: "latex suite \cite{ F9 does not work at all"
date: 2010-09-01
forum: Education &amp; Science
---

### Post by sky_yjl on 2010-09-01
I download the vim-latex-1.8.23-20100129-r1104.tar.gz from the soureforge net,
extract it into the $HOME/ .vim folder 
add these things into my .vimrc ,following the instructions said on the offical net

filetype plugin on
set shellslash
set grepprg=grep\ -nH\ $*
filetype indent on
let g:tex_flavor='latex'
let g:Tex_CompileRule_dvi='latex -src -specials -interaction=nonstopmode $*'
let g:Tex_ViewRule_dvi="xdvi -s 4 -fullscreen -editor 'gvim --servername latex-suite --remote-silent'" 

1 now&#65292;every function seem to work well except for the auto completion ,
every time after i typed \cite{ F9 ,nothing happened .

2. another problem is that \ref{ F9 can cause the apperance of the _outline_window,but the corresponding
key "n","p" which has been bound to the windows does not work

3 i use ubuntu 10.04 ,apt-get install vim-gtk,i have checked that my vim supports python.
Does anyone has similar problems? :confused:

---

### Post by xadder on 2010-09-01
I also tried this, some years ago, and gave up pretty quickly.

My day-to-day work is vim (without the latex-suite!), but I did find that gedit+latex plugin works pretty well, also with that kind of citation completion. Sometimes I use that just for a change.

---

### Post by sky_yjl on 2010-09-01
> **xadder said:**
> I also tried this, some years ago, and gave up pretty quickly.

My day-to-day work is vim (without the latex-suite!), but I did find that gedit+latex plugin works pretty well, also with that kind of citation completion. Sometimes I use that just for a change.

OK,I think emacs+preview would be a better choice.
But I love vim's fast speed command,and find latex-suite's
backward and forward searching works pretty well,and the only
flaw in my latex-suite is the citation completion, is this 
a bug? How can this software be updating for so many years 
without noticing this big problem?

---

### Post by FreeTheBee on 2010-09-01
I had this problem in windows a few weeks ago, in that case it turned out python was the problem. I had python 2.6, while vim needed 2.5. The new version 7.3 works with 2.7 though.
In Ubuntu it worked out of the box. But I assume these kind of issues are usually prevented by synaptic keeping track of dependencies. You could check if python works properly though by running something like :python print "test"

---

### Post by sky_yjl on 2010-09-01
> **FreeTheBee said:**
> I had this problem in windows a few weeks ago, in that case it turned out python was the problem. I had python 2.6, while vim needed 2.5. The new version 7.3 works with 2.7 though.
In Ubuntu it worked out of the box. But I assume these kind of issues are usually prevented by synaptic keeping track of dependencies. You could check if python works properly though by running something like :python print "test"

I don't think that is the point. I used python script a lot in my computer, nothing wrong had ever happend.
My vim has been installed through "apt-get install vim-gtk".Another friend said latex-suite works vergy well
on windows ,maybe it does not supports well for linux?

---

### Post by FreeTheBee on 2010-09-02
The smiley kinda ruined my suggestion. I tried to write the vim commmand. 

 :python print 'test' 

to see if python can be called correctly from within vim. Python as such also worked fine on my system, but not in Vim. I also doubt this is the problem, since the package manager should prevent these issues, but it only takes a second to check.
As I mentioned, for me it was the opposite, in Ubuntu everything worked right away, but windows gave me some problems. After installing matching versions of vim and python it works fine in windows as well.

---

### Post by sky_yjl on 2010-09-02
> **FreeTheBee said:**
> The smiley kinda ruined my suggestion. I tried to write the vim commmand. 

 :python print 'test' 

to see if python can be called correctly from within vim. Python as such also worked fine on my system, but not in Vim. I also doubt this is the problem, since the package manager should prevent these issues, but it only takes a second to check.
As I mentioned, for me it was the opposite, in Ubuntu everything worked right away, but windows gave me some problems. After installing matching versions of vim and python it works fine in windows as well.
Thanks.
the command
   python print 'test' can work in my vim.
There is one clue:
when i type \ref{ F9,the _outline_ window can pop up ,but when i type "n", it says "E486,can not find mode:
swbuff", Can this information help me?

---

