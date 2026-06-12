---
title: "GNU screen: Backspace thinks it's delete"
date: 2005-11-16
forum: Desktop Environments
---

### Post by unless on 2005-11-16
When I open GNU Screen, my backspace key doesn't work... It behaves like delete.

I tried adding the following line to my .screenrc...
```
bindkey -k kb stuff "177"
```

... But once I do that, I just get "177" echoed to the cmd line/screen every time I hit ^H (which is how I've been backspacing since the backspace key began its identity crisis).

"stty -a" outputs the following info (be it from within screen or not):
```
speed 38400 baud; rows 14; columns 144; line = 0;
intr = ^C; quit = ^\; erase = ^?; kill = ^U; eof = ^D; eol = <undef>;
eol2 = <undef>; start = ^Q; stop = ^S; susp = ^Z; rprnt = ^R; werase = ^W;
lnext = ^V; flush = ^O; min = 1; time = 0;
-parenb -parodd cs8 -hupcl -cstopb cread -clocal -crtscts
-ignbrk -brkint -ignpar -parmrk -inpck -istrip -inlcr -igncr icrnl ixon -ixoff
-iuclc -ixany -imaxbel
opost -olcuc -ocrnl onlcr -onocr -onlret -ofill -ofdel nl0 cr0 tab0 bs0 vt0 ff0
isig icanon iexten echo echoe echok -echonl -noflsh -xcase -tostop -echoprt
echoctl echoke
```

This is driving me nuts. I'm tired of seeing "Wuff Wuff!" every time I hit the backspace key.

Thanks in advance for any pointers.

---

### Post by levity on 2005-12-17
i have this problem too and don't know how to handle it either. what's even weirder is that a lot of "terminal graphics" (ncurses?) applications display messed-up. so far i've found problems with aptitude and w3m. the corruption only happens when i'm inside screen.

i've used screen on a bunch of different platforms, and ubuntu is the first i've encountered to show either of these problems.

---

### Post by HermanAB on 2005-12-17
Hmmm, have you tried:
$ stty sane

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by levity on 2005-12-18
Thanks for the suggestion, but that doesn't seem to change anything.

---

### Post by dare2dreamer on 2005-12-18
I've had several programs that run in screen get sorted out by the following:

export LANG=C

You might give it a shot. If it works, you can add it to .bashrc

---

### Post by zojas on 2006-01-09
no dice. man, this is annoying.

---

### Post by zojas on 2006-01-10
to expand on my last comment a bit:

I use zsh, and have it set to use vim-style command line editing rather than the default (emacs-style?)

when I'm in a shell in xterm or Konsole but not in screen, backspace works fine.

when I'm in a shell inside screen in konsole or on one of the text consoles, it also works fine.

but when I'm in a shell inside screen attached to xterm, hitting the backspace key backs up the cursor one position and puts me in command mode. if I hit backspace again, the character the cursor is sitting on top of is deleted, and the cursor backs up one more position. so the cursor ends up sitting on top of a character. it doesn't matter if I create  the screen session in the xterm or merely attach to an already existing screen session on the xterm.

---

### Post by zojas on 2006-01-10
found my problem: in /etc/X11/app-defaults/XTerm, there is a 'debian customizations' section.

in there, they have this line:

```
*backarrowKeyIsErase: true
```

I simply added this line to my ~/.Xdefaults to turn that off:

```
*backarrowKeyIsErase: false
```

then ran 

```
xrdb ~/.Xdefaults
```

launched a new xterm, re-attached to screen, and the backspace key worked as it should!!

---

### Post by zojas on 2006-04-03
normally I will attach to screen in an xterm.

I have recently found that if I have to type input to a program, the backspace key won't work. like if I type 'cat > /tmp/file', then type some text and hit backspace, it just echoes a ^H character. 

however, if I attach to screen inside konsole (the kde terminal), the backspace works fine when typing to cat.

backspace works fine with either terminal when typing to the shell directly.

---

### Post by hayalci on 2006-08-12
A simple solution from [http://lists.gnu.org/archive/html/screen-users/2006-05/msg00048.html](http://lists.gnu.org/archive/html/screen-users/2006-05/msg00048.html)

Set the TERM variable to screen before running screen.
```
TERM=screen screen
```
You can define an alias in your ~/.bashrc file like
```
alias screen='TERM=screen screen'
```

---

### Post by bps7j on 2006-10-04
None of the suggestions in this thread worked for me.  In the end, because I use XFCE's terminal emulator, I just went to the advanced preferences for it and selected that the backspace key should generate ^H.

---

### Post by hayalci on 2006-10-06
I have also discovered that xfce terminal works better. And, TERM=screen sucks also, TERM=vt100 may be more appropriate.

---

### Post by thetictacaddict on 2006-10-21
Hey, just wanted to say, this same thing has been bugging me as well.  Setting the option for Backspace = ^H worked, thanks!

---

### Post by unless on 2006-10-30
Good grief, I should've enabled email notification... I thought this thread had died a year ago.

As it turns out, I'd solved this problem, but, uh, I don't exactly remember how.

I may be dreaming, but I think I vaguely recall having found the TERM variable being explicitly set in the default ~/.bashrc (or maybe ~/.bash_profile). If you're having this problem, try looking there first, commenting out any lines that set TERM.

---

### Post by rustikus on 2006-12-10
Hi,

i have similar problems with screen. 
I use Midnight Commander inside of screen. 
The navigation works without problems but when i try to open a file with simply pressing return nothing happens. When i use mc without screen everything is fine.
Does somebody knows how to fix this?

EDIT: I think i should open a new topic.

---

### Post by x1a4 on 2007-02-26
> **unless said:**
> 

I tried adding the following line to my .screenrc...
```
bindkey -k kb stuff "177"
```

Change it to
```
bindkey -d -k kb stuff "\010"
```

Explicitly telling your terminal Backspace sends ^H is also a good Idea.  That's how I solved my screen backspace problem.

BTW when in screen I can't scroll using Shift+PgUp/PgDn, anyone know how to solve this?  Thank you.

---

### Post by Qew on 2007-02-26
> **x1a4 said:**
> 
BTW when in screen I can't scroll using Shift+PgUp/PgDn, anyone know how to solve this?  Thank you.

You can use the copy mode to scroll up and down screen. Ctrl+a+[ will put you in copy mode, then to get out of it, press Esc.

---

### Post by x1a4 on 2007-02-26
> **Qew said:**
> You can use the copy mode to scroll up and down screen. Ctrl+a+[ will put you in copy mode, then to get out of it, press Esc.

Yes I know, and I'm using it now, but I'm used to (and prefer) using Shift+PgUp/PgDn.  Screen's copy mode is a bit awkward, not only because I have to press three keys instead of two but also because it scrolls one line at a time instead of one page at a time.

---

### Post by unless on 2007-02-26
I know what you mean. Screen does lack the shift pgup/pgdown scroll feature that so many terminal programs offer. As far as I know there's no way to achieve it within screen.

However, screen's copy mode can be useful once you get used to it. And If you use vim, then it will take you no time to get the hang of it. Here are a few pointers.

First, in order to drop into copy mode, you can use ctrl-a esc rather than ctrl-a [. If you have a qwerty keyboard, that probably doesn't make a huge difference. But on many international keyboards, [ is a pain to type relative to esc.

Second, to scroll a screenful at a time (rather than line by line), use ctrl-b and ctrl-f.

If you're actually out to copy some text, you can quickly move to the top of the screen using H, to the middle using M, and to the bottom using L.

Then you can skip backwards and forwards a word at a time using b and w.

And, of course, the h, j, k, and l work as they do in vim to move the cursor (left, down, up, and right) if you're lazy like me and don't want to have to move your hand all the way over to the arrow keys.

hth.

---

### Post by jcDelta on 2008-07-10
If you're connecting from OSX, you'll need to set the terminal preference for "Send Ctrl-h on delete key"

---

