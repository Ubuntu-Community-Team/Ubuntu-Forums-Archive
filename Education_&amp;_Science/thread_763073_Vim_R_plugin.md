---
title: "Vim R plugin"
date: 2008-04-22
forum: Education &amp; Science
---

### Post by timbosity on 2008-04-22
HI,

this isnt an essential problem just something that Id like to fix. In short, Ive been using vim as my editor of choice for all things editable. It provides all I need and Ive gotten to quite like the modes and other quirks of vim. The one thing that swung my choice back when I was looking around for an all-purpose editor was the integration with R. This is where the vim-r plugin came in handy. Its worked perfectly for highlighting and sending lines, paragraphs and whole chunks of code over to a listening r interpreter open in an xterm. The vim plugin uses a perl script (funnel.pl) to send code through a pipe (as far as I understand).

Now, after some update (not sure what or exactly when but around 2 or 3 weeks ago), the piping stopped working. The F2 key which opened the listening R interpreter is still attempting to open R in new xterm (something like :! xterm -T 'R' -e funnel.pl ....) but its not working... Cant figure it out and so Ive reverted to the ol select and paste and using the mouse :shock:. It does mean I can have a nice R session (ie not in the minimalistic xterm :)) but my mouse finger is getting a little lazy...

So my questions:
1) does anyone else use this vim + rplugin set up?
2) does anyone have an idea as to why it would have stopped working?
3) any ideas how to fix it?

tim

---

### Post by timbosity on 2008-04-25
Obviously not:confused: how sad it was such a sweet as combination

---

### Post by akniss on 2008-04-25
I won't be of any help, but I thought I'd sympathize with you.  If ESS ever stopped working for me, I'd be rather despondent also...  I've really come to depend on emacs for my use of R.  I tried using Tinn-R on Windows a couple weeks back, and it seemed so inefficient compared to ESS now that I've gotten used to all the keystroke shortcuts.  Good luck getting things functioning again.

---

### Post by timbosity on 2008-04-26
Thanks for the sympathising. It must have done something because today, after a lengthy upgrading process (from gutsy to hardy: there were a few issues with this pc when I installed gutsy in the first place and the little issues popped up to say hello during upgrade), the little problem is fixed :guitar: hurrah for that. I have delved further and it was one of the perl libraries that had lost a dependency during some recent update...AND i realised that the vim-R plugin on my laptop at home had also stopped working. Upgrade is happening at the moment so hopefully all will be working smoothly next time I work at home!

---

### Post by webby35 on 2008-05-02
I use the vim-R plugin quite regularly on my Ubuntu (gutsy) laptop. It actually works quite well, since it is actually a little simpler when working directly on the laptop to push commands into R compared to all the Ctrl-clicking in ESS. I actually use both Emacs-ESS and gVim-R in my daily work, depending on my fancy. Sometimes, for my larger data sets, R takes forever to open within emacs, and basically makes Emacs hang. Vim-R works beautifully in this situation.  

 There are two bugs that I'm a little irritated with...
1. I have to start gvim first and then find the file for the <F2> to result in an R window. In other words, I just can't click on my R script file to open gvim and then use <F2>.
2. If I hit Ctrl-C in the R window, it shuts down the R window instead of stopping whatever is running, and the process continues to run in the background (so I have to find the process and kill it.

---

### Post by timbosity on 2008-05-02
i found that slightly annoying. Its just another thing to get used to...not doing a ctrl-c in R... I also havent managed to get Rhistory to work with the code sent to R from within vim. Any ideas?
i havent bothered with ESS because the vim set up is so easy on resources.

---

### Post by akniss on 2008-05-03
> **webby35 said:**
> it is actually a little simpler when working directly on the laptop to push commands into R compared to all the Ctrl-clicking in ESS. 

I'm curious... What are you ctrl-clicking?? I've not yet had to use the mouse to 'click' anything when using ESS.  That's the whole reason I started using ESS was the ability to work completely with the keyboard.

Ctrl+C Ctrl+N
Ctrl+C Ctrl+C
is really all I need...

---

### Post by webby35 on 2008-06-16
> **akniss said:**
> I'm curious... What are you ctrl-clicking?? I've not yet had to use the mouse to 'click' anything when using ESS.  That's the whole reason I started using ESS was the ability to work completely with the keyboard.

Ctrl+C Ctrl+N
Ctrl+C Ctrl+C
is really all I need...

Agreed. My language was a little off. What I meant was using the Ctrl key. Unfortunately, my laptop has a sensitive touchpad and using the Ctrl key often made my touchpad do weird things. With Vim-R, this was much less of an issue, which is why I use ESS when I have my laptop docked, and Vim-R when I have it on my lap :)

---

### Post by achristoffersen on 2009-03-06
I seem to have the same problem - only mine isn't resolved. As I am fairly new to linux I have no idea how to search for the solution. How did you upgrade exactly? 
 
BTW: posted my problem here: [http://www.nabble.com/R-and-vim-(gvim)-on-ubuntu-td22377215.html](http://www.nabble.com/R-and-vim-(gvim)-on-ubuntu-td22377215.html)

Sincerely,
Andreas

---

### Post by arkusk on 2009-09-10
Old thread but, there is a new vim plugin for R here [http://www.vim.org/scripts/script.php?script_id=2628](http://www.vim.org/scripts/script.php?script_id=2628).
Haven't tried it myself yet but it is actively being developed and looks promising.

---

