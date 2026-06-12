---
title: "Can't type / (slash) in terminal"
date: 2013-07-11
forum: Desktop Environments
---

### Post by PatriFernandez on 2013-07-11
Hi all!

Since I've updated ubuntu tu version 12.10 I can't type /, but just in terminal. I can type it in text editor, browser...anywhere but terminal. I've tried to fixing it by updating ubuntu to version 13.04 but it hasn't worked.

Any help is very much appreciated.

Regards.

---

### Post by alan9800 on 2013-07-11
it seems that something has been modified in the profile of the terminal. Do you have set a particular configuration?

---

### Post by PatriFernandez on 2013-07-11
No, Alan9800 I haven't any particular configuration :(

---

### Post by slickymaster on 2013-07-11
- Are you using a special, none normal keyboard?
- Have you set your keyboard correctly?
- Is your locale (region) setting correct?

---

### Post by sudodus on 2013-07-11
Are you talking about terminal window or terminal screen (full screen as via ***ctrl + alt + F1***)?

What language or locale are you using? Spanish?

what happens in a terminal window after the command

```
 setxkbmap es
```

or will it work with US English keyboard

```
 setxkbmap us
```

where / is typically on the key 'to the left of the right upper-case key'?

---

### Post by PatriFernandez on 2013-07-11
As I said, I can type / in everywhere except in ubuntu terminal. I have also tried to change keyboard configuration. My keyboard is normal and is the same I had before I update ubuntu. I'm using Spanish language but I also tried English with same result.

Thanks for all responses, I hope I get a solution sometime...

---

### Post by slickymaster on 2013-07-11
When you type the backslash character in the terminal, what character do you get?

---

### Post by sudodus on 2013-07-11
What do you mean by 'ubuntu terminal'?

Can you copy and paste a / from an editor to the terminal window? What happens?

Do you have problems with any other character?

Do you have problems only with one particular terminal window program, or is it a problem with ***bash***? You can try

xterm, gnome-terminal, lxterminal, konsole, ...

and the full screen (not window) via ***ctrl + alt + F1***

(return to the graphics session via ***ctrl + alt + F7***)

---

### Post by PatriFernandez on 2013-07-11
Slickymaster, I don't get nothing any character.

Sudodus, I mean just terminal, if i use full screen (crtl+alt+f1) it works . 

I copy a slash from text editor into my terminal and...nothing.

I've also tried Xterm and konsole and...nothing: No slash 

I can type \ but no / , and i don't have problem with no other character.

---

### Post by sudodus on 2013-07-11
This is very strange. Anyway, we can rule out bash, since it works in a text screen.

Is it like that also when you boot from a live CD/DVD/USB drive with some Ubuntu flavour and version 12.10 or 13.04?

This way we can find out if the problem is specific for your installed system, or if it is general for your locale or language (or computer but that is not very likely).

---

### Post by PatriFernandez on 2013-07-11
I agree sudodus this is very very strange. I have upgraded ubuntu to version 13.04 and same behavoiur...
I have discovered I can type / if first I press Insert (¿Why?) but is annoying because I have to press insert every time I want to type /
More strange if possible....

---

### Post by sudodus on 2013-07-11
At least you have a work-around now :-/ 
[COLOR=#000000]
Is it like that also when you boot from a live CD/DVD/USB drive with some Ubuntu flavour and version 12.10 or 13.04?[/COLOR]

---

### Post by slickymaster on 2013-07-11
Sorry for stepping in, guys, don't to pass as rude, but I though of asking PatriFernandez something. You aren't in a virtual machine environment, are you?

---

### Post by PatriFernandez on 2013-07-11
slickymaster:  No, It isn't a virtual machine.

Sudodus: When I boot a live cd it works, but I'd live to use my installation...

I really appreciate all your answers :)

---

### Post by steeldriver on 2013-07-11
I know sudodus kind of ruled out bash (based on the problem not appearing in the Ctrl-Alt-F1 virtual terminal) but do you have a ~/.inputrc file? if so what are its contents, may be a clue there

---

### Post by sudodus on 2013-07-11
If a live CD with 12.10 or 13.04 works (writing /), then there is something strange with your installed system. Something is eating your slash. Could it be that you have a hotkey link between / and some command, which is active only in the terminal windows?

You can create a new user, and check if the problem is there also for the new user. It might *not*, and in that case it is a user specific setting.

---

### Post by PatriFernandez on 2013-07-11
[**[COLOR=#000000]steeldriver[/COLOR]**]("http://ubuntuforums.org/member.php?u=1627500") I haven't a ~/.inputfile file.

[**[COLOR=#000000]sudodus[/COLOR]**]("http://ubuntuforums.org/member.php?u=1499021"): I have review if I had a hotkey linked but I haven't any... 
I haven't tried with another user but it still happens with root user.

---

### Post by sudodus on 2013-07-11
Yes, when you run root in a window created by your regular user id. It is rather easy to create a new user (and wipe it if you don't need it any more), so I suggest you try it, because it will help track where the cause can be. Use ***users-admin***. If you haven't got it, install it.

---

