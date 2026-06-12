---
title: "Konsole color scheme, Vim"
date: 2009-04-06
forum: Desktop Environments
---

### Post by street spirit on 2009-04-06
I'm having trouble with the colors in Konsole in KDE 4.2 (Kubuntu Intrepid). The colors used in Vim syntax highlighting are completely different from what I was used to in previous versions (KDE 3.x). This is what a test file with syntax highlighting in Vim looked like in the old Konsole (Hardy):

[IMG]http://foo.at/paste/2009/konsole_vim_hardy.png[/IMG]

I had tweaked the color scheme so that the text is more visible:

[IMG]http://foo.at/paste/2009/konsole_vim_hardy_custom.png[/IMG]

This is what the same file looks like in Intrepid's Konsole:

[IMG]http://foo.at/paste/2009/konsole_vim_intrepid.png[/IMG]

I wouldn't mind creating and adjusting a new color scheme, but the color mapping seems all wrong. If I change the cyan color of the comments to something less obtrusive, the identifiers change as well - I can't change the colors for the two separately. In addition to that, I can't turn off the bold font weight (who would want comments displayed in a bold font?). This was definitely possible in the previous Konsole incarnation. The old .schema color scheme files looked like this:

```
#   slot    transparent bold
#      | red grn blu  | |
#      V V--color--V  V V
color  0 220 203 178  0 0 # 0 - Foreground Color
color  1   0   0   0  1 0 # 1 - Background Color
color  2   0   0   0  0 0 # 2 - Color 0 (black)
color  3 206  29  29  0 0 # 3 - Color 1 (red)
...
```

There was a separate column for bold/normal display. The new .colorscheme files don't appear to support this setting anymore:

```
[Color0]
Color=0,0,0
Transparency=false

[Color0Intense]
Color=104,104,104
Transparency=false

[Color1]
Color=206,29,29
Transparency=false

[Color1Intense]
Color=255,84,84
Transparency=false
...
```

The old .schema files are still supported. They will become available  to select as color schemes, but the 'bold' setting is ignored. When you edit the color scheme with the GUI, a new .colorscheme file will be created to replace the old format.

I found out that I could bypass this problem (for now) by using the Andale Mono font, which doesn't have a bold style. It's not as pretty as the Monospace font, but at least it's not bold.

For reference, I [asked a similar question in the KDE forums]("http://forum.kde.org/konsole-configuration-color-schemes-t-40111.html"), where I learned that the problem was possibly related to adjustments made in Kubuntu. I spend so much time in Konsole that the syntax highlighting bug is a real problem for me. I've been using gvim (where the problem doesn't occur) because I find this so annoying. I'd be thankful for any hints and pointers how restore the old (and correct) behavior.

---

### Post by street spirit on 2009-04-06
I found out how to get the colors back the way I like them: put *set background=light* in Vim's color scheme file. Which is actually the wrong setting, because the Konsole background is black. /usr/share/vim/vimcurrent/colors/default.vim has the following lines at the top:

```
" Set 'background' back to the default.  The value can't always be estimated
" and is then guessed.
hi clear Normal
set bg&
```

Turns out vim was guessing the wrong background color all this time, which appears to have been fixed now, but in the meantime I've gotten used to the colors the way they were. In addition to that, if you leave the default setting, or use *set background=dark*, you get the problem with the comments/identifiers being the same color.

So... it's not a perfect solution, but it works for me.

---

### Post by ad_267 on 2009-05-25
Thanks for this! That helped a lot. It's weird that gnome-terminal seems to display them normally (or like I'm used to) if it's a problem with the vim colour scheme.

---

### Post by Josillo on 2009-07-01
Hello there!

I have the same problem.  Using Kubuntu 9.04, I normally set the Konsole profile to white on black (it's called "linux colors" exactly).

I'd like to use the "[oceandeep]("http://www.vim.org/scripts/script.php?script_id=368")" color schema.  It works fine in gVim and Pida IDE, but not in Konsole.

I don't understand clearly from your post if the line "set background=light" must be placed in the oceandeep.vim file, or in /usr/share/vim/vimcurrent/colors/default.vim, but I've tried both, and still haven't made it work.

Any ideas where I might be wrong? 
In wichw file did you put the "set background=light" line?  
Do you leave the "set background=dark" from vimrc commented or uncommented?


Thanks in advance for any help you may give!



Cheers.


Jose

---

### Post by street spirit on 2009-07-01
> **Josillo said:**
> I'd like to use the "[oceandeep]("http://www.vim.org/scripts/script.php?script_id=368")" color schema.  It works fine in gVim and Pida IDE, but not in Konsole.

Which part isn't working? The colors will never look the same in Konsole and in gVim, because the terminal only has limited color support. You can only choose from the existing colors, which in your case are set in /usr/share/kde4/apps/konsole/Linux.colorscheme .

> **Josillo said:**
> 
I don't understand clearly from your post if the line "set background=light" must be placed in the oceandeep.vim file, or in /usr/share/vim/vimcurrent/colors/default.vim, but I've tried both, and still haven't made it work.

Any ideas where I might be wrong? 
In wichw file did you put the "set background=light" line?  
Do you leave the "set background=dark" from vimrc commented or uncommented?


The oceandeep colorscheme already has "set background=dark", so you could try changing this to "light", but that will also affect gVim. If you want background=dark for gVim, and background=light in the Konsole, you could create a copy of the color scheme file, then use the one with background=light from your .vimrc, and the other from your .gvimrc.

HTH

---

### Post by Josillo on 2009-07-02
> **street spirit said:**
> Which part isn't working? The colors will never look the same in Konsole and in gVim, because the terminal only has limited color support. You can only choose from the existing colors, which in your case are set in /usr/share/kde4/apps/konsole/Linux.colorscheme .
HTH


Oh... Ok... 

That is the part that is not working!  My intention was to use the "oceandeep" color schema in "Konsole".

Reading [this post]("http://blog.cynapses.org/2006/08/09/konsole-256color/") I understood it was possible, but I can't find the "Session tab" mentioned there.  Tried adding the line 

"term        "screen-256color"

in my .kde/share/apps/konsole/Shell.profile file, but didn't work either.

So I guess if I want to use that color scheme I'll have to stick to gVim or Pida.


Thanks four your help and attention anyway!


Jose

---

### Post by street spirit on 2009-07-06
> **Josillo said:**
> Reading [this post]("http://blog.cynapses.org/2006/08/09/konsole-256color/") I understood it was possible, but I can't find the "Session tab" mentioned there.

That's interesting, I didn't know about the 256 color mode. The session tab was there in KDE 3.5, but I don't see it in 4.2 either. The folks over at the [KDE forums]("http://forum.kde.org/") probably know more about this. If you get it to work, please let me know.

---

### Post by krazyd on 2009-07-06
Konsole supports 256 colours, but vim doesn't recognise that so you have to tell it explicitly. add this to your ~/.vimrc:
```
set t_Co=256
```

Then get this script: [http://www.vim.org/scripts/script.php?script_id=2390](http://www.vim.org/scripts/script.php?script_id=2390)

It allows you to use _any_ colour scheme (even those written only for gvim) with vim in a console.

have fun!

---

### Post by NathanLT on 2009-08-17
Thanks krazyd, I was stuck with the same problem but your solution worked perfectly!

Nathan

---

