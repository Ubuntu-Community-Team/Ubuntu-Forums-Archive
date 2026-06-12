---
title: "Enter Euro symbol on US layout keyboard 23.04"
date: 2023-06-25
forum: Desktop Environments
---

### Post by grege2 on 2023-06-25
I need to be able to quickly enter currency symbols. I am an Australian and use the US keybord to get a $ sign as is normal here. But in my day to day use I also need the euro symbol. For the last decade I have just selected the English International with Euro on 5 keyboard layout and it has work fine. With Ubuntu 23.04 that option has evapourated and entering the euro symbol has been reduced to cut and paste. Older solutions like editing the keyboard with dconf no longer work, or at least not like they used to.

At the moment I have switched to the Cinnamon desktop that retains this functionality and I can quickly add a euro symbol with rgt-alt + 5

Does anyone know how to fix this. Old solutions do not work.

Edit:   English International with Euro on 5 can also be selected in Xubuntu. So it is just Ubuntu Gnome

---

### Post by TheFu on 2023-06-26
From the vim digraph notes.

```
char  digraph	hex	dec	official name 
€	Eu	**20AC**	8364	EURO SIGN
```

> EURO
							euro euro-digraph
Exception: RFC1345 doesn't specify the euro sign.  In Vim the digraph =e was
added for this.  Note the difference between latin1, where the digraph Cu is
used for the currency sign, and latin9 (iso-8859-15), where the digraph =e is
used for the euro sign, while both of them are the character 164, 0xa4.  For
compatibility with zsh Eu can also be used for the euro sign.


Don't know if this is helpful or not.  There's always unicode.

The exact program used to enter the symbol will matter since each seems to have their own solutions, including terminals.  Be certain your LANG setting is correct too.   With a correct LANG (some form of UTF8), 
```
echo -e '\u**20AC**'   
```
works.

There is no single answer. Welcome to the *bazaar* that is Linux. Other OSes provide a *Cathedral* experience, which in this specific case, seems like a much, much, much, better solution.

---

### Post by Holger_Gehrke on 2023-06-26
Entering Unicode in most programs is done by hitting ctrl-shift-u followed by the hexadecimal codepoint - 20ac in this case - and either space or enter. Entering '€' that way works in the browser, in the terminal, in LibreOffice Writer and Calc and probably in a lot of other programs. But that should only be a workaround for rarely used characters. For characters you use a lot, remapping the keyboard is probably the way to go. Sadly the (relatively) easy way to do this with 'xmodmap' won't work on Wayland (which is probably also the reason it works in XUbuntu but not in Gnome;  Gnome uses Wayland while XFCE isn't quite ready for that yet). Searching for 'Wayland keyboard remapping' on duckduckgo gives several hits that look promising.

Holger

---

### Post by grege2 on 2023-06-26
Thanks for the answers. Running a clunky command to run unicode will always work but it is impractical when you are typing in currency symbols all the time. I have switched to Xubuntu and now it is just alt-5 and no harder than shift-4 for the dollar sign.

To me this is just narrow thinking. Just because your local country uses dollars or euros or pounds does not mean that is all you use in your day to day work. Imagine being a travel agent using Ubuntu Gnome. Not for long!

---

### Post by grege2 on 2023-06-26
OK the answer is simple. Select US International keyboard. 

right-alt  5 = &#8364; and shift right-alt  4 = £

EDIT: Grrrr, US International is also missing from Ubuntu Gnome. It works well in Xubuntu and it looks like that is my new desktop.

---

