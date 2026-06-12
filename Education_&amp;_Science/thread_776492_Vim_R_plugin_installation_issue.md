---
title: "Vim R plugin installation issue"
date: 2008-04-30
forum: Education &amp; Science
---

### Post by samden on 2008-04-30
I am attempting to install the vim R plugin on Hardy, and am rather confused. I am not sure whether I have installed the plugin but can't figure out how to use it, or if it isn't installed at all.

I have:
- Installed R from the Ubuntu repositories
- Installed gVim using Synaptic
- added Johannes Ranke's Debian sid repository (deb [http://www.uft.uni-bremen.de/chemie/ranke/debs](http://www.uft.uni-bremen.de/chemie/ranke/debs) sid-jr/) to my /etc/apt/sources.list
- sudo apt-get update
- sudo apt-get install vim-r-plugin

Installation of the plugin seemed to go fine. However I don't see any option for it in vim. When in vim I:
- Change filetype to r (:set ft=r)
- Press F2. This should bring up a console running R, in theory. But the computer just beeps at me, and nothing happens.

More information on this plugin may be found at:
[http://www.vim.org/scripts/script.php?script_id=1048](http://www.vim.org/scripts/script.php?script_id=1048)
[http://www.uft.uni-bremen.de/chemie/ranke/?page=vim_R_linux](http://www.uft.uni-bremen.de/chemie/ranke/?page=vim_R_linux)

Do I just not understand how to use the plugin? Or has it not installed correctly? If anyone can offer any advice I would be most grateful. I am a complete novice on vim by the way, this is the first time I have used it.

---

### Post by peterff on 2008-04-30
I've also struggled with installing vim plugins. I noticed this section under "install details" on the first page:
> Note that you have to activate addons like this plugin since vim version
7.1-022+1, July 2007. For system-wide activation, use

$ vim-addons -w install r-plugin

(details in README.Debian).

Have you tried that? As an alternative, you might try downloading the archive on that page and extracting it to ~/.vim/plugins.

---

### Post by samden on 2008-04-30
Ok, that fixed it. Just made myself look a bit stupid there, didn't read the instructions properly!

Thanks heaps.

---

### Post by timbosity on 2008-05-01
Samden,

I see you got it fixed up :)
Good work. I had the same problem after upgrading to Hardy on laptop: ie the F2 key would no longer load an xterm with R running. Re-installing plugin with the system wide thing above got it fixed.

---

### Post by achristoffersen on 2009-02-24
Sorry - i don't know wether I should start a new thred, as this is already marked as 'solved'? Anyways - here goes:
When I:
```
vim-addons -w install r-plugin

```
I get
> Info: ignoring 'r-plugin' which is neither removed nor broken
Then in Vim (or gvim - tried both) I press F2 - nothing happens... Any ideas? 

Intripid

---

### Post by achristoffersen on 2009-02-24
If I open an r. script, go to visual-mode (v) and select some r-code and then press "r" i get this error message: "~/.r-pipe" E212: Can't open file for writing

Hope somebody can help

---

### Post by azvoleff on 2009-04-06
Same problem here. The plugin appears to be installed properly, except when I hit <F2> an xterm window opens and then immediately closes.

---

### Post by helmingstay on 2009-04-20
Instructions didn't quite work for me on gutsy or intrepid.

I used the etch-jr archive (deb [http://www.uft.uni-bremen.de/chemie/ranke/debs](http://www.uft.uni-bremen.de/chemie/ranke/debs) etch-jr/ ), all goes fine.  When i run "vim-addons -w install r-plugin" i get the following:

Warning: Ignoring unknown addons: r-plugin

I can copy or link the files manually from
 /usr/share/vim/addons/ftplugin/
to ~/.vim, and then everything works very well.  I edited r.vim to open gnome-terminal, which has a slightly different syntax...

***-T becomes -t, -e  becomes -x

"Start a listening R interpreter in new xterm
noremap <buffer> <F2> :!gnome-terminal -t 'R' -x funnel.pl ~/.r-pipe "R && echo -e 'Interpreter has finished. Exiting. Goodbye.\n'"&<CR><CR>

incidentally, my system-wide install of syntax/r.vim wasn't working from a previous .vim/filetype.vim entry, causing great confusion.  I had to change 
  au! BufNewFile,BufRead *.r,*.R        setfiletype R
to
  au! BufNewFile,BufRead *.r,*.R        setfiletype r

hope this helps.

---

### Post by jalvesaq on 2009-05-02
I'm developing a new plugin based on the work of Johannes Ranke. The plugin allows the user to kill R from vim. It also has omni completion of R objects and correct indentation of R code.

I think people reading this thread may be interested in testing the plugin and reporting bugs. The plugin is here: [http://www.vim.org/scripts/script.php?script_id=2628](http://www.vim.org/scripts/script.php?script_id=2628)

[IMG]http://jalvesaq.googlepages.com/vim-r-plugin2.png[/IMG]

---

### Post by Carambakaracho on 2009-05-10
I'm testing it. Glad someone keeps on developing that script.

---

### Post by azvoleff on 2009-05-12
I am also using the plugin for vim posted by jalvesaq. It is working well, and I appreciate your work. One issue I have had with it is the scrolling with using help() in R. Ordinarily R will allow vim keybindings to be used for scrolling a help file (for instance when using the R command "help(density)"). When I use the vim R plugin, however, neither vim keybindings nor arrow keys nor page up/page down will work to scroll help files in R. I am using gnome-terminal rather than xterm, if that makes any difference, with the latest version of the R plugin.

---

### Post by bgc on 2009-05-15
Hi,

I am also using the plugin provided by jalvesaq, and so far it's working well. I do have a related question though, which also applies to the previous version of the plugin: is there no way of getting a better GUI for R? I mean, compared to the Windows GUI, the xterm is not very good. It tends to truncate lines of code sent to it, colour coding for errors would be useful, and there's also the scrolling issue when consulting help files. As you have probably noticed by now I'm completely new to this, and just wondering if there are any things I can change to the setup to improve the experience! Any help or suggestions are very welcome! Thanks for any help you can give me, and for the great plugins!

bgc

---

### Post by samden on 2009-05-15
If you want a better GUI, you may want to try something other than vim. Rkward is an excellent GUI for R, JGR is another. Rkward is in the repositories (sudo apt-get install rkward), not sure about JGR.

Vim is for people who don't want a GUI!

---

### Post by jalvesaq on 2009-05-16
> **azvoleff said:**
> [...] One issue I have had with it is the scrolling with using help() in R. Ordinarily R will allow vim keybindings to be used for scrolling a help file (for instance when using the R command "help(density)"). When I use the vim R plugin, however, neither vim keybindings nor arrow keys nor page up/page down will work to scroll help files in R. I am using gnome-terminal rather than xterm, if that makes any difference, with the latest version of the R plugin.

I added a new key binding, <C-H>, which calls R's help().

The scroll issue affects both xterm and gnome-terminal. It seems that R doesn't use GNU Readline when called through a pipe. That's why you can't complete object names with <Tab> in the terminal window (and that's why I created the omni function for Vim). The best solution for me is to do "help.start()" in the terminal window before using help().

---

### Post by jalvesaq on 2009-05-16
> **samden said:**
> If you want a better GUI, you may want to try something other than vim. Rkward is an excellent GUI for R, JGR is another. Rkward is in the repositories (sudo apt-get install rkward), not sure about JGR.

Vim is for people who don't want a GUI!

Vim is for people who want an editor with advanced features, like complex search and replace, record of macros, etc. For those who prefer do not have to remember a lot of keyboard commands, it's better to use GUI for R like JGR or Rkward, as suggested by samden.

---

### Post by jalvesaq on 2009-05-16
> **bgc said:**
> [...] xterm is not very good. It tends to truncate lines of code sent to it, colour coding for errors would be useful [...].

I also would like to have color coding of errors in R's output, but I don't know how to get them without patching R source code.

The truncated lines are not a xterm limitation, but an issue with running R through a pipe (and I don't know how to solve it). However, although annoying, I don't see this problem as a serious bug because you still have the entire lines in the script that you are editing with Vim. You can also break the lines in Vim before sending them to R, and, in my opinion, the code will even become more readable.

As far as I know, the two most serious bugs of vim-r-plugin are:

(1) You should never hit Ctrl+C in the terminal window.
(2) Sending more than 4 k of text to R "obstructs" the pipe and freezes the terminal.

---

### Post by bgc on 2009-05-18
Hi! I fear I might have not explained myself very well! Sorry! So...

Samden: I'm actually very happy with Vim, and what I would want is not a GUI for Vim, but for R. And in fact, I think GUI isn't it either, just a somewhat better CLI (taking the better parts of the Windows implementation).

jalvesaq: Thank you for your reply! And thanks for the plugin! I only ask out of ignorance, because I have had situations where I would have wished something that turned out to be possible by tweaking settings! In any case this plugin allows me to stay away from Windows, so thanks.

---

### Post by jalvesaq on 2009-05-19
> **bgc said:**
> [...] I only ask out of ignorance, because I have had situations where I would have wished something that turned out to be possible by tweaking settings! In any case this plugin allows me to stay away from Windows, so thanks.

You are welcome! And, please, keep reporting bugs and wishes!

I can't fix the scrolling problem, but now the plugin calls R's help.start() automatically the first time that <C-H> is pressed. This behavior can be customized or even disabled, and the details are explained in the plugin's documentation. I think this is better than having to remember of calling help.start() manually.

The new version of the plugin has some other bug fixes:
[http://www.vim.org/scripts/script.php?script_id=2628](http://www.vim.org/scripts/script.php?script_id=2628)

---

### Post by bgc on 2009-05-20
That's great, and actually using help.start() or the method with the new version works great! I do have one question: how do you change settings, for instance the amount of indent (from 4 to 2 say)? Is it also possible to change any of the keybindings? Apologies in advance for probably very naive questions! Thank you!

---

### Post by jalvesaq on 2009-05-20
> **bgc said:**
> [...] I do have one question: how do you change settings, for instance the amount of indent (from 4 to 2 say)? Is it also possible to change any of the keybindings?

To change the amount of indent, put in your vimrc:

set shiftwidth=2

To change the key bindings you can open the file ~/.vim/ftplugin/r.vim and edit the lines that begin with "noremap", "inoremap" or "vnoremap". For example, in the following line you could replace <C-F9> with another key combination:

noremap <buffer> <C-F9> :call SendFunctionToR()<CR>

On the next weekend I will try to find a way of doing these settings in the vimrc, so you and other people will not have to patch the plugin after each new release.

---

### Post by jalvesaq on 2009-05-24
> **bgc said:**
> [...] Is it also possible to change any of the keybindings? [...]

I released a new version yesterday, and now it's possible to change the key bindings in the vimrc. There is also an option to choose the terminal emulator. The plugin's documentation has the details.

Is anyone editing the plugin to change its behavior? I would like to know because I could implement optional behaviors which would benefit people with different preferences.

---

### Post by bgc on 2009-06-03
Hi! Thanks for the plugin! Everything works fine as far as I can tell! Look forward to further progress, but so far happy with being able to use vim with R with very few issues indeed!

---

### Post by jalvesaq on 2009-06-04
> **bgc said:**
> Hi! Thanks for the plugin! Everything works fine as far as I can tell! Look forward to further progress, but so far happy with being able to use vim with R with very few issues indeed!

You are welcome! And, please, tell me if you have any idea of how to improve the plugin.

My TODO list is almost empty. I have to fix a small bug in code indentation and I could add a few more options like all vim buffers using the same pipe file and avoiding omni completion of zero length strings, but perhaps nobody needs these options.

The only improvement that I've made in my configuration that might be worth noting was the use of less as the default pager. I've created and made executable the file ~/bin/rpager with the following content:

```
#!/bin/sh

RHELPFILE="/tmp/R-help-$USER"
cat > $RHELPFILE
XTT=`head -n 1 $RHELPFILE | awk '{print $1}'`
xterm -T "$XTT - R Help" -e less $RHELPFILE &
```Then, I put in my .Rprofile:

```
if (interactive()) {
  local({
    options(editor='gvim -f -c "set ft=r"')
    options(pager="~/bin/rpager")
  })
}
```Now, the help system is usable even without calling 'help.start()'.

---

### Post by bgc on 2009-06-05
Well, the only issues are the ones you mentioned already: limit of how much code can be sent to R, colour coding of R (e.g. errors). Other than that I can't think of much, but then again I'm new to this so still in the discovery phase! But it's proving to be great not to depend on Win, Tinn-R, etc.!

---

### Post by bgc on 2009-06-08
Hi, I don't know if it is the indentation bug that you mention, but despite adding 'set shiftwidth=2' in the .vimrc file, the sw is 4 every time I open a file. Manually setting it in the file itself solves the issue.

---

### Post by jalvesaq on 2009-06-08
> **bgc said:**
> Hi, I don't know if it is the indentation bug that you mention, but despite adding 'set shiftwidth=2' in the .vimrc file, the sw is 4 every time I open a file. Manually setting it in the file itself solves the issue.

I also prefer shiftwidth=2. I commented out three lines of my ftplugin/r.vim that were there to increase compatibility with emacs (expandtab, shiftwidth, tabstop). I put a note in the documentation about these options. You will not have to edit the code again after the next release of the plugin!

The indentation bug happens when we have code like:

```
  if(T){
    a <- b
  }
  else {
}
```This is the code style shown when R prints a function content. I already fixed it here. I also fixed a bug in string recognition at "_" to " <- " conversion. I'll release the new version with these minor bugs fixed soon.

---

### Post by azvoleff on 2009-06-10
One useful feature would be a easy way to turn off the replacement of "_" with "<-", if desired. I have been having problems where I need to insert an underscore in the middle of a line. The help says to type an underscore twice when a real underscore is needed. Currently, hitting "_" twice in a row, when in the middle of a line, leads to the insertion of a "<-" at the original position of the cursor, and then the insertion of an "_" at the end of the line.

---

### Post by jalvesaq on 2009-06-10
> **azvoleff said:**
> One useful feature would be a easy way to turn off the replacement of "_" with "<-", if desired. I have been having problems where I need to insert an underscore in the middle of a line. The help says to type an underscore twice when a real underscore is needed. Currently, hitting "_" twice in a row, when in the middle of a line, leads to the insertion of a "<-" at the original position of the cursor, and then the insertion of an "_" at the end of the line.

Thanks for reporting the bug. I added the option that you requested. You may put in your .vimrc:

let g:vimrplugin_underscore = 1

But I believe that I fixed the bug and before using the option above you could test the underscore replacement in the new version of the plugin that I just released.

---

### Post by azvoleff on 2009-06-11
Thanks again for all of your work. The bug is fixed - the new version works as you described.

---

### Post by bgc on 2009-06-12
There's also something else I've noticed, although I'm not sure if it is me doing something wrong. If you open R through a file, then maybe close that R session and then try to send code to R (through some confusion, especially when working on more than one file), you get a message at the bottom of Vi saying ":call send block to R" and then seems to freeze.

It wouldn't happen if I kept track of what I open and with which file though!

Thanks for the new version!

---

### Post by jalvesaq on 2009-06-12
> **bgc said:**
> There's also something else I've noticed, although I'm not sure if it is me doing something wrong. If you open R through a file, then maybe close that R session and then try to send code to R (through some confusion, especially when working on more than one file), you get a message at the bottom of Vi saying ":call send block to R" and then seems to freeze.

It wouldn't happen if I kept track of what I open and with which file though!

Thanks for the new version!

You are welcome! Unfortunately, I don't know how to fix some bugs yet.

If you are using xterm, then, if you replace the line 76 of ftplugin/r.vim:
```
  let b:term_cmd = "uxterm -T 'R' -e"
``` with:
```
  let b:term_cmd = "uxterm -T 'R - " . bufname("%") . "' -e"
```The buffer name will be included in the xterm window title.

I can reproduce the bug that you described if I close the xterm by clicking in the "close" button at the xterm's title bar. The R process uses nearly 100% of the CPU and Vim freezes. Are you closing the xterm directly? R listens to a pipe file and not to xterm and outputs to xterm. So, it keeps running when xterm is closed, but can't output anything. R's quit() command is the better way of really closing R's session when using the plugin. (The other way is sending the INT signal from Vim).

---

### Post by bgc on 2009-06-12
I run the terminal instead of xterm. But there is a chance that what you say is true and that that happened/happens when I close the R session by closing the window. That's particularly likely if I have several open and end up confused as to what is what. I'll try to be more careful from now on and close the session as I should! Thanks for pointing it out!

---

### Post by bgc on 2009-06-16
This might be an irrelevant question in this context, so if it is I apologise in advance and feel free to ignore!

When setting filetype plugin on indent on, does that interfere with other plugins that may be installed for Vi? For instance, if I have Latex-Suite installed, do the two conflict, or is one or the other called depending on the file extension used?

Thanks!

---

### Post by jalvesaq on 2009-06-16
> **bgc said:**
> When setting filetype plugin on indent on, does that interfere with other plugins that may be installed for Vi? For instance, if I have Latex-Suite installed, do the two conflict, or is one or the other called depending on the file extension used?

They should never interfere with each other because each plugin is activated only for buffers of its specific file type. All key bindings include the keyword <buffer>, and even the menu items and ToolBar buttons should disappear when you switch from one buffer to another if they are not of the same type. However, you might have interference between your custom key bindings and some plugin key bindings, and this would be unfortunate, but not a bug.

If you find any conflict between the plugin key bindings and the default Vim key binding you may consider to report it as a bug to the plugin's developer (unless the conflict is documented as a "feature" of the plugin).

If you find any conflict between two plugins key bindings, then you've found a bug because probably someone had forgotten to put the <buffer> option while mapping the key.

It's also possible that we have a name clash of functions of the two plugins. In this case it would be a bug of vim-r-plugin because LaTeX-Suite is older, and because I didn't use the keyword <SID> in my functions. This keyword make the function unique to each script. Please tell me if have found any conflict.

---

### Post by bgc on 2009-06-17
OK, thanks. As far as I know there is no clash or there are no bugs, but I'm still moving on to get things working, including using vim for latex, and so wanted to make sure that no issues would arise because of this. If there were to be anything, I would let you (or them!) know! Thanks for the reply, and for developing the R plugin.

---

### Post by gunksta on 2009-08-05
The example setup for gnome-terminal was useful. Here's the equivalent for KDE users. This works from both gvim and vim.

```
let g:vimrplugin_term_cmd = "konsole --new-tab -e "
```

---

### Post by gunksta on 2009-08-07
I've noticed some interesting behavior in konsole when using the plugin and I' m curious to know if this behavior is seen in gnome-terminal. I start with one tab, running vim. I open a .r file and start up R using the new plugin. So far so good. My problems start when I try to open a third tab, using konsole's GUI. Rather than getting a terminal (fish is my default) I get another R session. Fortunately, if I use the menu and select a specific session, that works like it should.

Any thoughts on why this appears to interfere with konsole's default settings on this?

Note: At this point I'm still playing around with everything. This very well could be a konsole bug. I'm not sure. I thought I'd start here to get some feedback.

Thanks.

---

### Post by jalvesaq on 2009-08-07
> **gunksta said:**
> I've noticed some interesting behavior in konsole when using the plugin and I' m curious to know if this behavior is seen in gnome-terminal. I start with one tab, running vim. I open a .r file and start up R using the new plugin. So far so good. My problems start when I try to open a third tab, using konsole's GUI. Rather than getting a terminal (fish is my default) I get another R session. Fortunately, if I use the menu and select a specific session, that works like it should.

Any thoughts on why this appears to interfere with konsole's default settings on this?

Note: At this point I'm still playing around with everything. This very well could be a konsole bug. I'm not sure. I thought I'd start here to get some feedback.

Thanks.

I don't know what command opens a new tab in the current gnome-terminal window. Perhaps, it's not possible, and, thus, we cannot compare the two terminal emulators regarding this specific behavior. The following command opens a new window:
```
gnome-terminal --tab-with-profile=Default
```When I edit an R script with vim inside a gnome-terminal e press <F2>, and when the vim-r-plugin is configured to use gnome-terminal, It opens a new window, and I can normally open new tabs in both windows of gnome-terminal.

---

### Post by gunksta on 2009-08-08
> **jalvesaq said:**
> When I edit an R script with vim inside a gnome-terminal e press <F2>, and when the vim-r-plugin is configured to use gnome-terminal, It opens a new window, and I can normally open new tabs in both windows of gnome-terminal.

Thanks for the info.

I'll play with my configuration and tell vim to open a new instance of konsole. If this continues to cause odd behavior, I'll file a bug against konsole. The more I look at it, the more I believe this plug-in is exposing a subtle bug in konsole that is otherwise not noticed.

---

### Post by hugmenot on 2009-08-09
jalvesaq, In the last days I have been working with the author of the [screen.vim plugin]("http://www.vim.org/scripts/script.php?script_id=2711") to add a mode which opens a separate terminal window for more comfortable interaction.

He will will put this new release up this week and when that&#8217;s done I would encourage you to check it out and see if it&#8217;s not a better way of integrating vim and R than using the pipe method.

The pros:
[LIST][*]R can still be used normally, including completion and help browser (i.e., readline still works)[*]Starting and stopping R is implemented in a smart way and is very clean[*]Code necessary for integration is much less (no more funnel.pl, etc)[*]It is more flexible and not as limited (e.g. limit on characters sent at once)[*]It allows more cool things to be achieved, by manipulating the other terminal from within vim.[/list]

The cons:
[LIST][*]Does not work with Gvim. Only with terminals.
[/LIST]

I have made [a short video for him]("http://www.alice-dsl.net/~towolf/img/screen-vim.mpeg"), just as a proof of concept. It does not show what I did later to merge the R plugin and the screen plugin (mostly porting keybinding, BuildRtags(), etc, over to screen) for myself. We also got rid of the flicker when sending lines to the interpreter.

---

### Post by jalvesaq on 2009-08-09
> **hugmenot said:**
> jalvesaq, In the last days I have been working with the author of the [screen.vim plugin]("http://www.vim.org/scripts/script.php?script_id=2711") to add a mode which opens a separate terminal window for more comfortable interaction.

He will will put this new release up this week and when that’s done I would encourage you to check it out and see if it’s not a better way of integrating vim and R than using the pipe method.
[...]
I have made [a short video for him]("http://www.alice-dsl.net/%7Etowolf/img/screen-vim.mpeg"), just as a proof of concept. It does not show what I did later to merge the R plugin and the screen plugin (mostly porting keybinding, BuildRtags(), etc, over to screen) for myself. We also got rid of the flicker when sending lines to the interpreter.

The new approach is very good! GVim has a couple of advantages over plain Vim, but the perfect interaction with R achieved through the screen plugin makes its use far superior to the current approach of using funnel.pl. I will check the plugin when the new version is released, and certainly I will switch to it.

The main advantages of GVim is the availability of menus and buttons, which may make unnecessary the memorization of rarely used commands. Other advantage is the number of available colors, but we can use Vim with 256 colors. There are a few color schemes with support to 256 colors, and there is a perl script that helps to pick the colors most similar to the desired ones. I attached the script (I had to gzip it because the forum doesn't accept files with the pl extension).

---

### Post by jalvesaq on 2009-08-10
> **hugmenot said:**
> jalvesaq, In the last days I have been working with the author of the [screen.vim plugin]("http://www.vim.org/scripts/script.php?script_id=2711") to add a mode which opens a separate terminal window for more comfortable interaction.

[...]

The cons:
[LIST]
[*]Does not work with Gvim. Only with terminals.
[/LIST]
hugmenot, I released the last version of the plugin using funnel.pl and I'm now using screen, but it would be great if you or someone else could test the new version before I release it. To test the new plugin, please, gunzip the attached file and save it at ~/.vim/ftplugin/r.vim. It may be necessary to have the last released plugin installed because xterm is using an icon file available only in the last release.

The plugin works with both Vim and GVim, but not directly with gnome-terminal. To run R inside gnome-terminal, it's necessary to start it within xterm, detach the session (C-a C-d), and run screen in gnome-terminal ("screen -r").

I'm not using the screen.vim plugin; instead, I adapted the functions of vim-r-plugin to use screen. So, there is no difference in usage for users of vim-r-plugin.

Thanks!

---

### Post by hugmenot on 2009-08-11
Just wanted to say that the new version of screen.vim is out on vim.org.

In your version I noticed some things:
[LIST=1]
[*]It&#8217;s possible to start an instance of R with each press of F2. Things fail from then on. You shouldn&#8217;t spawn more than one instance. Myself, I use this technique » screen -d -RR -S Arrr R «
[*] Why do you say screen doesn&#8217;t work with gnome-terminal? It works very well here.
[*] Here is a suggestion for the .screenrc:
```
termcapinfo xterm* 'ti@:te@'
```
With this you are able to scroll the R output naturally. With the mousewheel or with Shift-PgUp/Down
 [*] some of your keybindings don&#8217;t work here. E.g., <C-F9> or <M-Enter>.
[/LIST]

---

### Post by jalvesaq on 2009-08-11
> **hugmenot said:**
> Just wanted to say that the new version of screen.vim is out on vim.org.Great! I'll try it.
> 
In your version I noticed some things:
[LIST=1]
[*]It’s possible to start an instance of R with each press of F2. Things fail from then on. You shouldn’t spawn more than one instance. Myself, I use this technique » screen -d -RR -S Arrr R «
[*] Why do you say screen doesn’t work with gnome-terminal? It works very well here.
[*] Here is a suggestion for the .screenrc:
```
termcapinfo xterm* 'ti@:te@'
```With this you are able to scroll the R output naturally. With the mousewheel or with Shift-PgUp/Down
[*] Some of your keybindings don’t work here. E.g., <C-F9> or <M-Enter>.
[/LIST]

[LIST=1]
[*]Thanks! -d -RR solved the problem! If you prefer that different R scripts use the same R process, please, put in your .vimrc: let g:vimrplugin_single_r = 1
[*]It was a typo in my script. I was using "-x" instead of "-e".
[*]Thanks for the suggestion. It's even better now.
[*]<C-F9> is working here, but <M-Enter> isn't working to me too. I've switched from <S-Enter> to <M-Enter> because the first only worked with GVim and the second only with Vim. I'll go back to <S-Enter> since it at least works with GVim. You can choose another combination in your .vimrc:
[/LIST]

---

### Post by gunksta on 2009-08-11
I saw all this talk about screen.vim and I installed it and I really like it. It seems like a neat way to work for a number of reasons that have nothing to do with R. That being said, will the new R.vim plugin conflict with screen.vim or will they peaceably co-exist?

---

### Post by jalvesaq on 2009-08-11
> **gunksta said:**
> [...] will the new R.vim plugin conflict with screen.vim or will they peaceably co-exist?
I think that there will be no conflict between them, and if we find any conflict, we can solve it. I still have to look more carefully at screen.vim to see what improvements I can make in the vim-r-plugin.

---

### Post by gunksta on 2009-08-11
Does it make sense to make the R plug-in dependent on screen.vim? It looks like screen.vim is experiencing quite a bit of development right now. 

It would make installation and set-up slightly more difficult, but I don't think it would be prohibitive to anyone willing to use vim in the first place.

---

### Post by jalvesaq on 2009-08-11
> **gunksta said:**
> Does it make sense to make the R plug-in dependent on screen.vim? It looks like screen.vim is experiencing quite a bit of development right now. 

It would make installation and set-up slightly more difficult, but I don't think it would be prohibitive to anyone willing to use vim in the first place.
I'll have time to explore the screen.vim only on the next weekend. Then, I might discover new interesting features and may adopt it since I don't want to reimplement every screen.vim feature into r-vim-plugin. However, currently there are only two lines of r.vim that runs screen: (1) to start R; (2) to send a line of code to R.

---

### Post by hugmenot on 2009-08-11
> **gunksta said:**
> Does it make sense to make the R plug-in dependent on screen.vim?

In theory, it would be possible. But the mechanics of r.vim are slightly different from a UI perspective. This pertains to how many lines are sent and how the send command reacts to a visual selection, etc. I guess for old users that wouldn&#8217;t be optimal.

In the end what screen.vim does to send text is just calling screen like this:

screen -X stuff "<text to be sent>"

Try it out! And r.vim can do that just as well. Wrapping the original vim buffer itself in a screen is less useful when you open a new terminal window anyway and not a split.

What we found out just today is that there is a string length limit on the » screen -X « notation of around 4096 characters. This is similar to the original limitation with the R plugin using a pipe. But we already found a way around that. It should be on vim.org soon.

---

### Post by jalvesaq on 2009-08-11
> **hugmenot said:**
> What we found out just today is that there is a string length limit on the » screen -X « notation of around 4096 characters. This is similar to the original limitation with the R plugin using a pipe. But we already found a way around that. It should be on vim.org soon.
I've just released the first version of vim-r-plugin using screen, and I believe that it isn't affected by the 4096 characters problem because the lines are sent separately, even when the whole file is sent to R.

---

### Post by hugmenot on 2009-08-12
Eric, on the other hand, solved the character limitation like this

```
  let tmp = tempname()
  call writefile(lines, tmp)
  try
    let result = system(
      \ 'screen -p ' . g:ScreenShellWindow .  ' -X eval ' .
      \ '"msgminwait 0" ' .
      \ '"readbuf ' . tmp . '" ' .
      \ '"at ' . g:ScreenShellWindow . ' paste ." ' .
      \ '"msgminwait 1"')
  finally
    call delete(tmp)
  endtry

```

That is, he writes the lines to be sent to a temp file and then has screen read it into the paste buffer and paste it.  So, it writes a file each time, but screen is only called once.

---

### Post by jalvesaq on 2009-08-12
> **hugmenot said:**
> That is, he writes the lines to be sent to a temp file and then has screen read it into the paste buffer and paste it.  So, it writes a file each time, but screen is only called once.
Eric's solution is more efficient. I'll adapt his code to vim-r-plugin, but first I'll wait some days for feedback on the current version of the plugin.

---

### Post by bgc on 2009-08-13
Hi! Thanks for the updates! I'm not sure if and what I'm doing wrong though, but when I try to open an R interpreter, I get a dialog saying "Cannot open child process" and it hangs. I've just put the most recent version. Am I doing anything wrong? Do I also need to install the other screen plugin for vim for it to work?

Thanks!

---

### Post by jalvesaq on 2009-08-13
> **bgc said:**
> Hi! Thanks for the updates! I'm not sure if and what I'm doing wrong though, but when I try to open an R interpreter, I get a dialog saying "Cannot open child process" and it hangs. I've just put the most recent version. Am I doing anything wrong? Do I also need to install the other screen plugin for vim for it to work?

I guess that you didn't do anything wrong. The problem was that I've put a wrong information in the older versions of the plugin documentation.

Do you have the option g:vimrplugin_term_cmd set in your .vimrc? In older versions of the plugin I was using the parameter "-x" in the example of how to set gnome-terminal as the terminal emulator to run R. The parameter "-x" works for funnel.pl, but with screen we need "-e". You can simply delete g:vimrplugin_term_cmd from your vimrc because gnome-terminal is the default terminal now.

Does this information solve your problem?

---

### Post by bgc on 2009-08-14
Yes, that seems to have solved it. Thanks!

---

### Post by jalvesaq on 2009-08-28
Hi,

I released a new version of the plugin with just a little change in the screenrc file that the plugin uses so that the startup is faster.

For people editing Rnoweb files, the plugin now jumps to the next '^<<' when the line sent to R is '^@$'. I believe that the plugin is stable now.

I've tried to use temporary files to send large blocks of code, but sometimes the code sent from the plugin mixed with R's output and the R interpreter got spurious lines.  So, the plugin still uses the slower technique of send lines one by one when sending a block of code or the entire file to R.

---

### Post by PGScooter on 2009-08-30
thank you jalvesaq! I can't wait to install the vim R plugin once I get a few other things taken care of.

---

### Post by jalvesaq on 2009-10-05
Hello!

I released a new version of the plugin. The author of Tinn-R now is co-author of the plugin and we added many new key bindings, restructured the menu and created new Tool Bar buttons. NOTE: some old key binding changed, including the shortcut to start R. Please report any problem with the plugin:

[http://www.vim.org/scripts/script.php?script_id=2628](http://www.vim.org/scripts/script.php?script_id=2628)

---

### Post by Carambakaracho on 2009-10-05
I just discovered the new version on vim.org, but haven't tested it yet. Anyway I wanted to congratulate you for this excellent work. 

In my opinion best thing you did was switching from funnel.pl to screen which solved mayor issues I had with the R plugins before and makes this really useful to me. I'll promote it in the German Ubuntu community ;)

Carambakaracho

---

### Post by gunksta on 2009-10-05
This is a real improvement. Unfortunately, all of the new key-bindings break my current cheat-sheet. 

I've got some time to kill today at work. I will re-work my vim cheat-sheet and stick it up here in a new thread. Maybe someone will find it useful.

---

### Post by Carambakaracho on 2009-10-06
Darn it, omni-completion needs grepl of R > 2.9.0, do I get that right?

I'm working with 2.6.2 and upgrading results in incompatibilities in dependencies a discontinued R package.

Other problems I encountered
Whenever I'm trying \sw it'll enter in substitute character mode, isn't that implemented yet? Just got the idea after I saw there's no menu entry for that neither...

For the key bindings I'd suggest to exchange all the commands without echo and commands with echo in order to get echo on <f9> and non on <F9>. My idea behind that is that during writing a script I'm frequently running a few lines but I'd like to trace what I already did. While running the whole file or working chunks when you don't need output is less frequent.

Great work, I love the new functions, that's really going to be very useful once I memorized the key bindings and don't have to look in the help file all the time... 

Carambakaracho

---

### Post by gunksta on 2009-10-06
I would like to second Carambakaracho's thoughts on the keybindings. While I think mapping the echo and non-echo versions to the same key makes a lot of sense, I will want echo more often than I will want to avoid it (in the latter case, I usually just source("myfile.R")).

f9 = with echo
F9 = without echo

would be easier to use.

---

### Post by jalvesaq on 2009-10-06
> **Carambakaracho said:**
> Darn it, omni-completion needs grepl of R > 2.9.0, do I get that right?

I'm working with 2.6.2 and upgrading results in incompatibilities in dependencies a discontinued R package.

I'm sorry for that! Perhaps you could edit the file .vim/tools/rtags.R to use grep and post the diff here. Alternatively, wouldn't it be possible to fix the discontinued R package? 

> 
Other problems I encountered
Whenever I'm trying \sw it'll enter in substitute character mode, isn't that implemented yet? Just got the idea after I saw there's no menu entry for that neither...It's implemented and working for me: \sw runs Sweave(), but it's only available if the filetype is rnoweb (.Rnw). The key binding isn't activacted for .R files.

> 
For the key bindings I'd suggest to exchange all the commands without echo and commands with echo in order to get echo on <f9> and non on <F9>. My idea behind that is that during writing a script I'm frequently running a few lines but I'd like to trace what I already did. While running the whole file or working chunks when you don't need output is less frequent.Initially, I also preferred the echo because this was the way I was used to. However, the source function has one limitation and one problem: The limitation is that errors and warnings are printed in the screen only after all the code is sourced. The other problem is the output of an extra '\n" after each command. The extra "\n" is located at line 142 of source(). With these two problems, I didn't see it advantageous the use of echo.

Anyway, you can map the keys to work like you want. I just noticed that there are two <Plug>KBindingNames wrongly written in the plugin, but you can try putting the following in your vimrc (perhaps the result is what you want):

map <S-F9> <Plug>RDSendSelection
imap <S-F9> <Plug>RDSendSelection
vmap <S-F9> <Plug>RDSendSelection
map <F9> <Plug>REDSendSelection
imap <F9> <Plug>REDSendSelection
vmap <F9> <Plug>REDSendSelection


>  
Great work, I love the new functions, that's really going to be very useful once I memorized the key bindings and don't have to look in the help file all the time...Thanks!

---

### Post by gunksta on 2009-10-09
After playing with the rpager.sh file, I'd like to add a line (for those of us on KDE).
```

 konsole --new-tab -p tabtitle="R Help - $XTT" -e less $RHELPFILE & 

```

But, then I got to thinking that really, using programs like konsole, xterm, etc. all share the same fundamental weakness. They would have to be set for EACH user. Someone on gnome will want something different from someone on KDE, who will want something different from someone on XFCE.

This is essentially the same problem dealt with setting the vimrplugin terminal in the first place, but it's not necessary here. If someone wants to look at R-help, they are probably already running R which means they are running screen.

Now, this is VERY rudimentary, but it does start going in the right direction.

```

    screen -X split && screen -X focus && screen -X screen && screen -X exec less $RHELPFILE

```

This will essentially do what I want, although there are some definite problems with it. Another alternative is to remove the split and focus and then simply call screen to make a new . . . screen and pipe the pager info through it.

Or perhaps the best idea is to make an extra keybinding so that one version (the default) will make a new screen while the alternative will split the screen.

I'm going to play with this some more. I'll post a rpager.sh file later this weekend.

---

### Post by gunksta on 2009-10-09
Take Two - This works better I think.

```

    screen -X screen && screen -X exec less $RHELPFILE && screen -X title "R Help - $XTT"

```

It opens up a new screen, which gets a useful name, and then runs less. Unfortunately, when you hit "q" and leave the pager, you are dropped down to the bash prompt. I need to figure out a way to force this prompt to immediately kill itself. Not sure how to do that part yet. A user can still do this with CTRL-a k, but it's a little weird to go from a pager to bash, for no apparent reason.

---

### Post by jalvesaq on 2009-10-09
> **gunksta said:**
> It opens up a new screen, which gets a useful name, and then runs less. Unfortunately, when you hit "q" and leave the pager, you are dropped down to the bash prompt. I need to figure out a way to force this prompt to immediately kill itself. Not sure how to do that part yet. A user can still do this with CTRL-a k, but it's a little weird to go from a pager to bash, for no apparent reason.

I didn't test your code, but would the addition of exit work? Something like

```
"less rhelp.txt ; exit"
```

---

### Post by gunksta on 2009-10-09
> **jalvesaq said:**
> I didn't test your code, but would the addition of exit work? Something like

```
"less rhelp.txt ; exit"
```


I tried something similar to that earlier and couldn't get it to work, which is why I didn't include it in what I posted up here. The problem seems to be in the order I have to put things. It seems like screen needs the title of the screen to be the last command, which causes problems, because that means the "; exit" part gets lost and never run.

There may be an easy way out of/around this. I do not claim to be a screen expert.

---

### Post by gunksta on 2009-10-10
This works better.

```

 screen -X screen less $RHELPFILE && screen -X title "R Help - $XTT"

```I've also noticed a problem with the new version of the rplugin. If I'm using GVim, things work as expected. But if I'm using Vim, it still starts a new instance of my terminal and starts screen up in that which is a little confusing. It would be more consistent with ScreenShell if the rplugin recognized the fact that Vim was running in a terminal already and split things up from there.

EDIT: I just noticed that this is not perfect. If I use the screen profile in Ubuntu, all is good. If I use the default one in the rplugin, it does not.

---

### Post by jalvesaq on 2009-10-11
> **gunksta said:**
> I've also noticed a problem with the new version of the rplugin. If I'm using GVim, things work as expected. But if I'm using Vim, it still starts a new instance of my terminal and starts screen up in that which is a little confusing. It would be more consistent with ScreenShell if the rplugin recognized the fact that Vim was running in a terminal already and split things up from there.

EDIT: I just noticed that this is not perfect. If I use the screen profile in Ubuntu, all is good. If I use the default one in the rplugin, it does not.

I think that you would be happier if vim-r-plugin used screen plugin to communicate with R. I could add options to: (1) start R with the command :ScreenShell R; (2) send commands to R with :SendString. The problem is that the command :SendString doesn't exist in the screen plugin. It can send only selected lines or the entire file, but the vim-r-plugin do more than that. For example, it can send the command "summary(anRobject)" if the cursor is over the word anRobject.

---

### Post by gunksta on 2009-10-11
> **jalvesaq said:**
> I think that you would be happier if vim-r-plugin used screen plugin to communicate with R. I could add options to: (1) start R with the command :ScreenShell R; (2) send commands to R with :SendString. The problem is that the command :SendString doesn't exist in the screen plugin. It can send only selected lines or the entire file, but the vim-r-plugin do more than that. For example, it can send the command "summary(anRobject)" if the cursor is over the word anRobject.

Lately I've been using screen a lot. Being able to detach and attach to sessions is incredibly cool. It's especially nice as I use an aging laptop to do development on a much newer server which I use to actually run Postgres and R. I can run smaller projects locally, but when I'm playing with big state-wide data sets, my laptop is simply inadequate.

A few months ago, I was using EMACS, but struggled with ESS hanging randomly and often EMACS would not send the entire file to Postgres or R for processing. After fighting with that for a while, I gave up on EMACS. I don't need to use a tool of that complexity if it's going to hang the system.

A friend introduced me to screen and it was incredibly useful. I missed some of the keybindings and tricks from EMACS, but the utility of screen made up for it. ScreenShell and VIM are no replacement for the ESS mode in EMACS, but they do provide some of the functionality after tossing in a few key bindings.

When you announced that you had this idea of rewriting the rplugin to use screen, I was definitely excited. I guess my point isn't that I care either way about the screen plugin, but I would like it if the rplugin integrated smoothly with existing screen sessions, because screen is becoming an integral part of my work-flow. 

That interest in integrating the rplugin with screen is why I started playing around with using screen itself as the rpager, which is something that I definitely think is possible (and really kinda cool).

I guess I need to take the time to look more carefully at your rplugin and ScreenShell to see what the differences are in structure and see if I can come up with some ideas.

---

### Post by Carambakaracho on 2009-10-14
Sorry for the late answer.

> **jalvesaq said:**
> 
Perhaps you could edit the file .vim/tools/rtags.R to use grep and post the diff here.


```
 Building 'tags' file for vim omni completion.
Error in if (haspunct[1]) { : argument is not interpretable as logical
```
I'm not surprised as this is what is the difference according to the man pages. I tried to fix it but was somewhat unsuccessful up to now. It's not very important anyway as I'm not programming all the time. 
> 
Alternatively, wouldn't it be possible to fix the discontinued R package?

Another package has taken over the functions and it's just a matter of adapting the code to the different data structure. I haven't had the time to do that yet and I there was no need to do it so far.
> 
It's implemented and working for me: \sw runs Sweave(), but it's only available if the filetype is rnoweb (.Rnw). The key binding isn't activacted for .R files.

Oh, well I'm not yet very familar with that Latex stuff, sorry.
> 
Anyway, you can map the keys to work like you want.

So I did like you described above, it works like a charm. Thank you.

---

### Post by jalvesaq on 2009-10-16
Hi!

I uploaded a new version of the plugin. Now the integration with the screen.vim plugin is possible and consequently it's possible to use it in the Linux console or other environment without the X Server.

NOTE 1: The screen.vim plugin is optional. You don't need to install it if you always use vim or gvim in a graphical enviroment.

NOTE 2: It's necessary to use a version of screen.vim released a few days ago to integrate both plugins.

NOTE 3: The Send key bindings changed because the Fn keys do not work as expected in all circumstances.

---

### Post by bgc on 2009-11-17
Hi! Thanks for the updates, they work great! I have a couple of questions (I'm not sure if I should be doing so here or not):

Is there a way of setting rnoweb and R files differently? I guess a simple solution would be to create the rnoweb.vim file in .vim/ftplugin/ rather than keep it as a linked file as it is now.

Also, I am unsure on how to get vim-r-plugin and latex-suite to interact when using noweb files. Right now at least it seems to be a choice of either one or the other. Does anyone have any ideas or suggestions?

Thanks!

---

### Post by jalvesaq on 2009-11-17
> **bgc said:**
> Is there a way of setting rnoweb and R files differently? I guess a simple solution would be to create the rnoweb.vim file in .vim/ftplugin/ rather than keep it as a linked file as it is now.

Also, I am unsure on how to get vim-r-plugin and latex-suite to interact when using noweb files. Right now at least it seems to be a choice of either one or the other. Does anyone have any ideas or suggestions?

If we create a real rnoweb.vim file, it will be necessary to maintain two scripts, which is more error prone than maintaining just one. What features do you want disabled when the file type is rnoweb? I can add options to disable these features.

I don't use latex-suite, but I've already tried it a couple of years ago, and I remember that it has too many key bindings. Perhaps you could remap the vim-r-plugin key bindings that conflict with the latex-suite ones that you need. The vim-r-plugin documentation explains how to customize the plugin key bindings.

---

### Post by bgc on 2009-11-18
Thanks for the reply. Well, the kind of things I was thinking of are hardly applicable to most people. I just wanted to have a textwidth=80 option for R files, but not for latex/noweb files.

With respect to latex-suite / vim-r-plugin interaction, the thing is that none of the latex-suite keybindings work. But that has probably more to do with latex-suite not working on Rnw files I suspect. I am, however, unsure about how to tell vim to load both latex-suite and vim-r-plugin for Rnw files.

BTW, how do you deal with latex files? Just a makefile?

Thanks for the help!

---

### Post by gunksta on 2009-11-18
Relevant to this thread, is this posting from REvolution Computing discussing ESS. Don't know how many of you follow the REvolution Computing blog and thought you might find this interesting.

[http://blog.revolution-computing.com/2009/11/installing-ess-on-ubuntu.html](http://blog.revolution-computing.com/2009/11/installing-ess-on-ubuntu.html)

I threw in a comment  at the bottom, offering the rplugin as another option for Linux users.

I do have to wonder though why he took a screen-shot of the non-GTK EMACS. EMACS isn't exactly a thing of beauty, but that screen-shot makes things look worse than necessary.  ;)

---

### Post by jalvesaq on 2009-11-18
> **bgc said:**
> Thanks for the reply. Well, the kind of things I was thinking of are hardly applicable to most people. I just wanted to have a textwidth=80 option for R files, but not for latex/noweb files.

You may put in your .vimrc (of course, change the value from 76 to what you want):

autocmd BufNewFile,BufRead *.tex set tw=76
autocmd BufNewFile,BufRead *.Rnw set tw=76

> **bgc said:**
> With respect to latex-suite / vim-r-plugin interaction, the thing is that none of the latex-suite keybindings work. But that has probably more to do with latex-suite not working on Rnw files I suspect. I am, however, unsure about how to tell vim to load both latex-suite and vim-r-plugin for Rnw files.

You can try:[FONT=Verdana]

[/FONT]autocmd BufRead,BufNewFile *.Rnw set filetype=tex

Reference: [http://stackoverflow.com/questions/1504318/associate-rnw-with-vim-latex-suite](http://stackoverflow.com/questions/1504318/associate-rnw-with-vim-latex-suite)

But I guess that the vim-r-plugin will stop working, unless you make it a global plugin (see the plugin documentation).[/quote]

> **bgc said:**
> BTW, how do you deal with latex files? Just a makefile?

If the .tex or .Rnw inputs other .tex or .Rnw files, I use a Makefile. And I added the following line to my .vimrc to deal with such .Rnw files:

nmap <LocalLeader>sm :update<CR>:call SendCmdToScreen('system("make")')<CR>

If it is a single .tex, I simply type "pdflatex filename.tex" in the terminal emulator. If it's a single .Rnw, I use the plugin shortcuts (\sw and \sp).

---

### Post by jalvesaq on 2009-11-18
> **gunksta said:**
> I threw in a comment  at the bottom, offering the rplugin as another option for Linux users.

Thanks!

---

### Post by bgc on 2009-11-19
Thanks for the info and suggestions! It might be worth just scrapping latex-suite as I'm not really sure how useful it is!

Cheers!

---

### Post by jalvesaq on 2009-12-23
Hello!

I've just released a new version of the plugin with the following three main changes:

(a) Syntax highlight of R functions.
(b) Use of a scratch window to display function's arguments during omni completion.

Because of the extra information it's necessary much more time to build the R tags file. The solution was to split the tags file in two: one for objects in .GlobalEnv and another for all other objects (loaded with the R libraries). Thus, the third change:

(c) It's necessary to load the libraries that you usually use (in R) and then use the command  :RUpdateObjList (in Vim) to highlight functions and to include in omni completion objects that are not loaded by vanilla R. This command have to be used only once because the tags file is permanently stored at ~/.vim/tools. You only need to run it again if you want to include functions and other objects of additional libraries.

The documentation has the details. Please, tell me if you find any bug introduced with the new features.

---

### Post by gunksta on 2009-12-23
Just loaded it up and everything looks good at first blush. I'm doing QA for a bunch of data we just entered so I won't be able to use it much today. If I find any bugs I'll let you know.

---

### Post by SabreWolfy on 2010-05-10
@jalvesaq

Thanks for vim-r-plugin2! :)

After following the installation instructions, I ran **:RUpdateObjList**, which waited for 30 seconds and then died, saying something about updating when next I opened a .R file. I quit vim and opened a .R file but nothing happened. I ran the command again, but it gave an error immediately. What is this command for and do I need to run it? Edit: Found the details in the help file; not sure I understand them all, but I don't think I need to run this at the moment. Thanks :)

Does the plugin provide any syntax highlighting? I notice that normal R commands and lines beginning with # appear in the same colour, which is quite confusing ...

---

### Post by jalvesaq on 2010-05-10
> **SabreWolfy said:**
> 
After following the installation instructions, I ran **:RUpdateObjList**, which waited for 30 seconds and then died 

This is a bug in the plugin. I wrongly supposed that 30 seconds would be enough to everyone, but if your computer is slower or if you have much more libraries loaded than I supposed one would have, you will need more than 30 seconds. I will either increase this value or create a new variable to control it. For now, you can manually edit the file ~/.vim/ftplugin/r.vim and increase the number 90 in the first of the following three lines (it's at line 677 in my r.vim version):

    if i == 90
      call delete(locktagsfile)
      call RWarningMsg("Thirty seconds is too much: no longer waiting.")

I did another minor mistake. 90 * 250 miliseconds are just 22.5 seconds...

> **SabreWolfy said:**
> 
What is this command for and do I need to run it?

This command is needed to: (1) syntax highlight of function names and (2) omni completion.

> **SabreWolfy said:**
> 
 Does the plugin provide any syntax highlighting? I notice that normal R commands and lines beginning with # appear in the same colour, which is quite confusing ...

Yes, it improves the syntax highlight that Vim already has for R files. Only functions need the RUpdateObjList to be highlighted.

---

### Post by SabreWolfy on 2010-05-11
Thanks for the detailed reply.

How do I go about changing the highlighting then? All R commands appear the same colour as # comments. The instructions to add R objects mentions using the library() command. At the moment I'm just using the standard R commands. Are those already added? Why are the functions not highlighted then?

---

### Post by jalvesaq on 2010-05-11
> **SabreWolfy said:**
> How do I go about changing the highlighting then? All R commands appear the same colour as # comments. The instructions to add R objects mentions using the library() command. At the moment I'm just using the standard R commands. Are those already added? Why are the functions not highlighted then?

If you are only using standard R commands, you should do nothing because the plugin already ships with a ~/.vim/tools/rfunctions file listing all functions of vanilla R. This file may have been deleted by the :RUpdateObjList command, then, you should reinstall the plugin to recover the rfunctions file. However, even without the rfunctions the syntax highlight should be normal; only functions would not be highlighted. In fact, even without the plugin, you should have syntax highlight of R files because this is a standard feature of Vim provided by:

   /usr/share/vim/vim72/syntax/r.vim

Do you have these two lines in your ~/.vimrc files?

filetype plugin on
filetype indent on

What happens if you do the following command in Vim while editing an R file:

:set filetype

It should return filetype=r

Do you have either vim-gnome or vim-gtk installed? Standard Ubuntu comes with vim-tiny which doesn't have syntax highlight capabilities.

---

### Post by SabreWolfy on 2010-05-11
Thanks for the reply.

> **jalvesaq said:**
> If you are only using standard R commands, you should do nothing because the plugin already ships with a ~/.vim/tools/rfunctions file listing all functions of vanilla R. This file may have been deleted by the :RUpdateObjList command, then, you should reinstall the plugin to recover the rfunctions file.

The **rfunctions** file is present.

> **jalvesaq said:**
> However, even without the rfunctions the syntax highlight should be normal; only functions would not be highlighted. In fact, even without the plugin, you should have syntax highlight of R files because this is a standard feature of Vim provided by:

   /usr/share/vim/vim72/syntax/r.vim

Do you have these two lines in your ~/.vimrc files?

filetype plugin on
filetype indent on


**/usr/share/vim/vim72/syntax/r.vim** is present. Both lines are present in **~/.vimrc**.

> **jalvesaq said:**
> What happens if you do the following command in Vim while editing an R file:

:set filetype

It should return filetype=r


Yes, it shows **filetype=r**.

> **jalvesaq said:**
> Do you have either vim-gnome or vim-gtk installed? Standard Ubuntu comes with vim-tiny which doesn't have syntax highlight capabilities.

**vim-gnome** is installed.

Thanks for the help. I'll remove the plugin and see what changes. If highlighting is still not working, then it has nothing to do with the plugin.

---

### Post by SabreWolfy on 2010-05-11
(I did not have a ~/.vim folder before installing the plugin, so I made the folder and installed the plugin.)

I renamed ~/.vim folder to something else and R syntax highlighting *worked*. I renamed the folder back to ~/.vim and R functions are highlighted in the same way as comments, which makes code very difficult to read.

I deleted .vim and reinstalled the plugin from the the .tar.gz file into ~/.vim. Highlighting is not working properly. I ran the ":helptags" command, but not the ":RUpdateObjList" command. I confirmed that some of the functions I am using are found in the "rfunctions" file.

---

### Post by SabreWolfy on 2010-05-11
PS: I notice that the plugin uses the location of the file opened as the working folder for R -- very nice! :) So doing this:

```

$ cd ~
$ vim /some/long/path/file.R
```

and then opening an R session sets R to use "/some/long/path" as the working directory, which is exactly what I need. :)

---

### Post by jalvesaq on 2010-05-11
> **SabreWolfy said:**
> (I did not have a ~/.vim folder before installing the plugin, so I made the folder and installed the plugin.)

I renamed ~/.vim folder to something else and R syntax highlighting *worked*. I renamed the folder back to ~/.vim and R functions are highlighted in the same way as comments, which makes code very difficult to read.

I deleted .vim and reinstalled the plugin from the the .tar.gz file into ~/.vim. Highlighting is not working properly. I ran the ":helptags" command, but not the ":RUpdateObjList" command. I confirmed that some of the functions I am using are found in the "rfunctions" file.

Is the highlighting problem only with functions? If your answer is yes, my only guess is that your color scheme uses the same color for comments and functions. Could you please look at your color scheme script (theses scripts are located at /usr/share/vim/vim72/colors/).

---

### Post by SabreWolfy on 2010-05-12
> **jalvesaq said:**
> Is the highlighting problem only with functions? If your answer is yes, my only guess is that your color scheme uses the same color for comments and functions. Could you please look at your color scheme script (theses scripts are located at /usr/share/vim/vim72/colors/).

I'm using the default vim colorscheme (which appears to be the same as "ron") with ":background=dark". Comments and functions are different colors when vim-r-plugin2 is not installed. When it is installed, comments and functions are the same color. Setting background=light or changing color scheme makes comments and functions different colors.

---

### Post by jalvesaq on 2010-05-12
> **SabreWolfy said:**
> I'm using the default vim colorscheme (which appears to be the same as "ron") with ":background=dark". Comments and functions are different colors when vim-r-plugin2 is not installed. When it is installed, comments and functions are the same color. Setting background=light or changing color scheme makes comments and functions different colors.

I couldn't reproduce the bug, but I uploaded the current version of the plugin. Could you please install it? Then, we would be using exactly the same version:

[http://www.vim.org/scripts/script.php?script_id=2628](http://www.vim.org/scripts/script.php?script_id=2628)

---

### Post by Resting_stage on 2010-05-20
Sorry, but I can't get the vim-r-plugin2-100512 to work on XUbuntu 10.04 with Xfce. When I press the 'Start R' button in gvim (vim-gtk) the command :call StartR("R") is issued, but nothing happens. R works fine on its own. I've installed this plugin on Ubuntu 9.04 and 9.10 and Elive Topaz 2.0 (another Debian based distro) and it always worked fine. I also installed the plugin on a fresh XUbuntu 10.04 live distro, just to make sure that I did not screw any settings beforehand. There it did not work either. Screen is installed. Any suggestions???

Many thanks!

---

### Post by jalvesaq on 2010-05-20
> **Resting_stage said:**
> Sorry, but I can't get the vim-r-plugin2-100512 to work on XUbuntu 10.04 with Xfce. When I press the 'Start R' button in gvim (vim-gtk) the command :call StartR("R") is issued, but nothing happens. R works fine on its own. I've installed this plugin on Ubuntu 9.04 and 9.10 and Elive Topaz 2.0 (another Debian based distro) and it always worked fine. I also installed the plugin on a fresh XUbuntu 10.04 live distro, just to make sure that I did not screw any settings beforehand. There it did not work either. Screen is installed. Any suggestions???

I installed xfce4-terminal here and it seems that the problem is the option "-t" which no longer exist. Could you please try to replace "-t" with "--title" at line 302 of ~/.vim/ftplugin/r.vim and let me know it works?

---

### Post by Resting_stage on 2010-05-21
Replacing -t with --title solved the problem. Many thanks!!!

---

### Post by jalvesaq on 2010-05-21
> **Resting_stage said:**
> Replacing -t with --title solved the problem.

Thanks! I uploaded a new version with bug fixed.

---

### Post by jalvesaq on 2010-07-28
Hi!

I've built a Debian version of the plugin:
[http://sites.google.com/site/jalvesaq/vimrplugin](http://sites.google.com/site/jalvesaq/vimrplugin)

If you are interested in testing it, please, tell me if you find any bug.

---

### Post by SabreWolfy on 2010-07-29
> **jalvesaq said:**
> Hi!

I've built a Debian version of the plugin:
[http://sites.google.com/site/jalvesaq/vimrplugin](http://sites.google.com/site/jalvesaq/vimrplugin)

If you are interested in testing it, please, tell me if you find any bug.

Thanks! Can this safely be installed over an existing installation?

---

### Post by jalvesaq on 2010-07-29
> **SabreWolfy said:**
> Thanks! Can this safely be installed over an existing installation?

The plugin installed in your home directory will have priority if you enable the plugin system wide with vim-addons. So you would still be using an old version. If you try to use vim-addons to enable the plugin just to yourself, vim-addon will report that the installation is broken. In both cases you can use vim-addons to remove the conflicting files and, then, enable the new version:

```
vim-addons remove r-plugin
vim-addons install r-plugin
```Only the files that are in both the new and the old version of the plugin will be removed by the vim-addons remove command. Depending on the version that you were using there may be other files. They are harmless but if you want to delete them you would have to remove them manually.

NOTE: I changed the name of the addon to r-plugin to make it shorter. The Debian package is still named vim-r-plugin.

---

### Post by Carambakaracho on 2010-09-10
Hi jalvesaq,

I just tried the latest version compatible with vim 7.0 (vim-r-plugin2-100803.zip) but I get the following errors on sending more than one line to R:

```
Error detected while processing function SendSelectionToR..RSourceLines:
line    1:
E121: Undefined variable: b:rsource
E116: Invalid arguments for function writefile
line    9:
E121: Undefined variable: b:rsource
E15: Invalid expression: "source('" . b:rsource . "')"
line   11:
E121: Undefined variable: rcmd
E116: Invalid arguments for function SendCmdToScreen(rcmd)
E15: Invalid expression: SendCmdToScreen(rcmd)
line   12:
E121: Undefined variable: ok
E15: Invalid expression: ok

```

There is another error message on launching gvim with a R file, but it's gone too fast to read or copy it and I've no clue how to make it reapear...

I'm using Vim 7.1 together with R 2.6.1 on a Ubuntu 8.04 machine. Going back to vim-r-plugin2-100710 works perfectly fine, no errors and everything works properly. There are four versions between I didn't test, if you already have an idea what this is about that's fine, otherwise I'm open to try the intermediate versions, too.

Carambakaracho

---

### Post by il_principe on 2010-09-12
I have used Stata and gVim on Windows for a while  now. Recently I have switched to Ubuntu, and I am planning to also change  from Stata to R.
  A friend of mine is using R and Emacs ESS which seems to work  perfect, however i'd rather like to keep using vim. I have installed the  vim-r-plugin2, however, i can only send code to a seperate terminal  running R. I would much rather split my screen into a buffer running R  and one buffer with my .R file, and then send code from one to the  other. With ESS in Emacs this seems to work, you can run a terminal/R in  a buffer without a problem. I haven't found a way to make this work in vim. The only way to open a buffer  running a shell I could find is the Conque Shell plugin, but this is not supported by the vim plugin.
  I know that unlike Emacs, Vim is designed to be a simple text editor.  However, having R run in a buffer seems just so much more practical. Is there any way to do this?

---

### Post by jalvesaq on 2010-09-12
> **Carambakaracho said:**
> Hi jalvesaq,

I just tried the latest version compatible with vim 7.0 (vim-r-plugin2-100803.zip) but I get the following errors on sending more than one line to R:

```
Error detected while processing function SendSelectionToR..RSourceLines:
E121: Undefined variable: b:rsource

```There is another error message on launching gvim with a R file, but it's gone too fast to read or copy it and I've no clue how to make it reapear...

I'm using Vim 7.1 together with R 2.6.1 on a Ubuntu 8.04 machine. Going back to vim-r-plugin2-100710 works perfectly fine, no errors and everything works properly.

Your Vim 7.1.138 does not have the getpid() function which was introduced in 7.1.262. The next release will contain a workaround, but you can use the current version if you edit ~/.vim/ftplugin/r.vim and find and delete the . getpid() 

You can see past messages with the command:
:messages

I can't release the new version yet because it's currently broken on Windows.

---

### Post by jalvesaq on 2010-09-12
> **il_principe said:**
> [...] i can only send code to a seperate terminal  running R. I would much rather split my screen into a buffer running R  and one buffer with my .R file, and then send code from one to the  other. [...] The only way to open a buffer  running a shell I could find is the Conque Shell plugin, but this is not supported by the vim plugin.
  I know that unlike Emacs, Vim is designed to be a simple text editor.  However, having R run in a buffer seems just so much more practical. Is there any way to do this?

Did you try to install the screen.vim plugin? Please see:
:h vimrplugin_screenplugin

With the screen plugin enabled in the vim-r-plugin, if you are running vim in a terminal emulator, \rf will split the terminal window in two regions, one with Vim and the other with R, and you can go from one region to another hiting Ctrl+A+Tab. This is not the same thing as having R running in a Vim's buffer but at least it's visually similar.

I didn't know about the Conque Shell plugin. I'll look at it.

---

### Post by il_principe on 2010-09-12
I've tried it with screen, but i really prefer to use the gui version of vim (also i couldnt figure out how to split the window vertically using screen). i've also posted this question on stackoverflow, and somebody posted a fixed version that supports the conque shell plugin. ive only tried it superficially, but it seems to work. if you want to have a look, here's the link 
[http://stackoverflow.com/questions/3692988/running-r-inside-a-buffer-in-vim](http://stackoverflow.com/questions/3692988/running-r-inside-a-buffer-in-vim)

cheers,

orange

---

### Post by jalvesaq on 2010-09-12
> **il_principe said:**
> I've tried it with screen, but i really prefer to use the gui version of vim (also i couldnt figure out how to split the window vertically using screen).

You can use tmux instead of screen. It supports vertical split. Install the screen plugin:

   [http://www.vim.org/scripts/script.php?script_id=2711](http://www.vim.org/scripts/script.php?script_id=2711)

Put in your vimrc:

  let vimrplugin_screenplugin = 1
  let g:ScreenImpl = 'Tmux'

You will have to learn how to use tmux...

>  i've also posted this question on stackoverflow, and somebody posted a fixed version that supports the conque shell plugin. ive only tried it superficially, but it seems to work. if you want to have a look, here's the link 
[http://stackoverflow.com/questions/3692988/running-r-inside-a-buffer-in-vim](http://stackoverflow.com/questions/3692988/running-r-inside-a-buffer-in-vim)

I'm trying to add support to the conque shell plugin but the integration with the vim-r-plugin isn't that good yet.

---

### Post by Carambakaracho on 2010-09-13
> **jalvesaq said:**
> Your Vim 7.1.138 does not have the getpid() function which was introduced in 7.1.262. The next release will contain a workaround, but you can use the current version if you edit ~/.vim/ftplugin/r.vim and find and delete the . getpid() 

You can see past messages with the command:
:messages

I can't release the new version yet because it's currently broken on Windows.

Don't worry, as far as I'm concerned I'm perfectly fine with the version 100710 which enormously improved compared to the version I used previously. My system's anyway pretty outdated but some of the not yet published analysis rely on some old R libraries. 

By the way, is there a way to make the vim R plugin communicate with another (more recent) R release compiled into /home or /opt? And not necessarily available in the alternatives.

Thank you.
Carambakaracho

---

### Post by jalvesaq on 2010-09-13
> **Carambakaracho said:**
> 
By the way, is there a way to make the vim R plugin communicate with another (more recent) R release compiled into /home or /opt? And not necessarily available in the alternatives.

The last version has the option vimrplugin_r_path. Currently, this variable must contains the complete file path of the R executable, but this may change on the next release to the directory where R is located.

---

### Post by jalvesaq on 2010-09-17
> **jalvesaq said:**
> I'm trying to add support to the conque shell plugin but the integration with the vim-r-plugin isn't that good yet.

The integration is improving, and the new version of the vim-r-plugin (100917) works better with the development version of Conque Shell.

---

### Post by jalvesaq on 2010-10-15
Hello! The Vim-R-plugin has a new feature: object browser. You may want to try this new version... Please report any bugs. Thanks!

---

### Post by bgc on 2010-11-16
Hi,

Thanks again for the plugin! It is of great help. I have a question on indentation: I hope it hasn't already been covered...

The Google code-style page for R suggests using curly brackets as follows:

```
for (i in 1:100) {
  print(i)
}
```


And that works fine with the plugin. However if you prefer to follow a more conventional style, such as:

```
for (i in 1:100)
{
  print(i)
}
```

then vim doesn't seem to deal with indentation very well, and it all goes a bit mad from there. Is this down to the indentation style of the plugin, or is it due to some other reason?

Many thanks!

---

### Post by jalvesaq on 2010-11-16
> **bgc said:**
> Hi,
Thanks again for the plugin! It is of great help. I have a question on indentation: I hope it hasn't already been covered...

[...] then vim doesn't seem to deal with indentation very well, and it all goes a bit mad from there. Is this down to the indentation style of the plugin, or is it due to some other reason?


The plugin doesn't do a perfect job indenting R code. I've made minor improvements in the indentation script in the last weekend, but didn't release the new version yet. Could you please email me. So I would send to you the version that is being developed and you could check whether the problem remains. Thanks!

---

### Post by snesterko on 2011-01-28
Hi,

Thank you so much for your work on this. I have decided to switch from textmate to vim for my R development, and the plugin is extremely useful for that.

But just following up on the previous post, the indentation is not perfect, and the only thing that separates it from being great is indenting the arguments of function declarations and function calls that do not fit in a single line.

I have used ESS with emacs for considerable time before, and the indentation of R code there is just perfect. That seems to be the only software that does it. There are hacks that allow to use ESS indentation in textmate, and this is what I have been doing.

I understand that the indentation as of now in vim-R-plugin is ok, and there could be other important issues to deal with, but please consider that improving it to at least correct multiline function argument indentation would save a significant amount of time.

Thanks again for great work!

---

### Post by jalvesaq on 2011-02-03
> **snesterko said:**
> [...]
I have used ESS with emacs for considerable time before, and the indentation of R code there is just perfect. That seems to be the only software that does it. 

[...]

I understand that the indentation as of now in vim-R-plugin is ok, and there could be other important issues to deal with, but please consider that improving it to at least correct multiline function argument indentation would save a significant amount of time.


I released a new version improving the indentation, including alignment of function arguments. A few bugs in the indentation of R code remain, but some of the differences between the way ESS and Vim-R-plugin indent code are intentional. For example, Vim-R-plugin and ESS indent differently the following code:

```
for(i1 in list1)
    for(i2 in list2)
        for(i3 in list3)
            for(i4 in list4)
                cat(i1, i2, i3, i4, "\n")
```The variables r_indent_ess_comments and r_indent_ess_compatible make the indentation a bit more similar to the one done by ESS.

People that prefer the old style of indentation of function arguments, should put the following in their vimrc:

```
let r_indent_align_args = 0
```

The section 10.8 of the plugin's documentation explains the details.

---

### Post by snesterko on 2011-02-14
Thank you !

I got the updated version of indentation, and it seems to be working like a charm!

I have another quick, very minor question. Please feel free to ignore it in case this is too basic (as I am indeed new to vim). Here it is:

Is there support of automatically creating ## comment symbols when going to a new line from a commented line? For example, in case I am typing comments like this

##            this is a comment, but it is too long, so I'd like to go to another line right now<CR>

is there a way to have ## inserted on new line automatically, and the cursor being aligned with the first letter of 'this', on the second line?

Does this question make sense at all? In any case, thank you so much for indentation, this works great.

---

### Post by jalvesaq on 2011-02-14
> **snesterko said:**
> Is there support of automatically creating ## comment symbols when going to a new line from a commented line?

The last version, 110208, released on February, 8, do it, because I added the following option to ftplugin/r.vim:

setlocal comments=b:#,b:##,b:###

---

### Post by snesterko on 2011-02-14
Somehow this doesn't work for me.. I am on a Mac, and use simple Vim-R, with your syntax and indent files, and also rsyntax and functions files.

I took those two lines from the ftplugin/r.vim file, and copied them into syntax file, to no effect. Maybe, this was too naive?

Also, the syntax folding is an amazing feature, but seems to have some bugs. For example, when in insert mode, Shift-9 will unfold all folds in the buffer.

Thank you so much for you hard work on the plugin.

---

### Post by SabreWolfy on 2011-02-14
**@jalvesaq:** Just another thank-you for this plugin. It works perfectly and I use it often. :D

---

### Post by jalvesaq on 2011-02-14
> **snesterko said:**
> Somehow this doesn't work for me.. I am on a Mac, and use simple Vim-R, with your syntax and indent files, and also rsyntax and functions files.

I don't know if the Mac version of Vim is compiled with support to auto format the lines as they are typed, but I suppose it is.

> **snesterko said:**
> I took those two lines from the ftplugin/r.vim file, and copied them into syntax file, to no effect. Maybe, this was too naive?

Any option may be in any file. The effect is the same, unless you have different values in different files. Then, the last one will prevail. See  :h --startuptime  to know the order in which the scrips are read.

The automatic formating of the line is controlled by 'formatoptions'. Do you have this variable set in your vimrc? Please, see  :h 'formatoptions' for details.

> **snesterko said:**
> Also, the syntax folding is an amazing feature, but seems to have some bugs. For example, when in insert mode, Shift-9 will unfold all folds in the buffer.

Nothing happens here when I type Shift-9. I use zi in Normal mode to fold/unfold all folds. Please, see   :h zi

I my keyboard, Shift-9 is the open parenthesis key: '('. Did you map the key ( to something in your vimrc?

---

### Post by snesterko on 2011-02-14
Thanks for the response. I dont' know what is wrong. '(' must be then mapped to, or in conflict with something on my macvim. But in insert mode, repeated '(' has weird behaviour. Press double (, and folds unfold. This is a little bizarre, but I am not sure where to look for a solution.

For the comments, I have tormatoptions=tcq, and comments=b:#,b:##,b:### when I am editing a file. This should work, but it doesn't. I don't know how to address this, but will look into this further. Thank you for your help and hard work on this.

---

### Post by jalvesaq on 2011-02-14
> **snesterko said:**
> Thanks for the response. I dont' know what is wrong. '(' must be then mapped to, or in conflict with something on my macvim. But in insert mode, repeated '(' has weird behaviour. Press double (, and folds unfold. This is a little bizarre, but I am not sure where to look for a solution.

For the comments, I have tormatoptions=tcq, and comments=b:#,b:##,b:### when I am editing a file. This should work, but it doesn't. I don't know how to address this, but will look into this further. Thank you for your help and hard work on this.

Perhaps you could start by making a backup of your current ~/.vimrc and test whether a very simple vimrc works. Below is an example of simple vimrc:

```
set nocompatible
syntax enable
filetype plugin on
filetype indent on
let r_syntax_folding = 1
set nofoldenable
autocmd FileType r setlocal formatoptions=cq

```If the above works, you could add new options, copying them from your original vimrc...

---

### Post by snesterko on 2011-02-17
Thanks for the response!

No, that doesn't work. I replaced the settings in my .vimrc with what you have recommended, and the behaviour is unchanged. There is no autocommenting and the ( has weird behaviour.

For autocommenting, it works for say .vim files, where " is the comment symbol, but doesn't for R files. This is bizarre.

---

### Post by jalvesaq on 2011-02-17
> **snesterko said:**
> No, that doesn't work. I replaced the settings in my .vimrc with what you have recommended, and the behaviour is unchanged. There is no autocommenting and the ( has weird behaviour.

For autocommenting, it works for say .vim files, where " is the comment symbol, but doesn't for R files. This is bizarre.

That's really strange! Do you have anything in ~/.vim/after/ftplugin/r.vim ?

Another test would be to make a backup of your .vim directory, delete the directory and then create a new one with just the Vim-R-plugin inside. Anyway, it seems that you are the only person experiencing this weird bug. Since I can't reproduce the bug, I can't be more helpful.

---

### Post by SabreWolfy on 2011-02-24
I have **.RData** and **.Rhistory** under version control for some work I am busy with. After updating my local copy of the files on a second machine, I launched **vim** and hit F2. The screen window appeared briefly (empty) and them immediately closed.

I launched **R** in the folder and it returned an error message about a package not being installed and then terminated. I solved this by simply launching **R** from another folder and installing the missing package.

Is it possible for the plugin to detect/trap this condition and somehow report it? My initial thought was that the plugin was broken.

---

### Post by jalvesaq on 2011-02-27
> **SabreWolfy said:**
> I have **.RData** and **.Rhistory** under version control for some work I am busy with. After updating my local copy of the files on a second machine, I launched **vim** and hit F2. The screen window appeared briefly (empty) and them immediately closed.

Could you please provide a sample script that would create such a problematic workspace?

---

### Post by SabreWolfy on 2011-03-01
Package P is installed on Computer 1. A .R file is then edited. At some point, Package P is loaded into the workspace. The workspace is saved (into a version control folder). The folder is updated to the repository.

On Computer 2, the local copy is updated so the new workspace is now present. The same .R file is edited and F2 is pressed to load R. R loads in the folder where the workspace is saved and attempts to load the existing workspace. This workspace requires Package P which is not installed on Computer 2.

---

### Post by jalvesaq on 2011-03-01
> **SabreWolfy said:**
> Package P is installed on Computer 1. A .R file is then edited. At some point, Package P is loaded into the workspace. The workspace is saved (into a version control folder). The folder is updated to the repository.

On Computer 2, the local copy is updated so the new workspace is now present. The same .R file is edited and F2 is pressed to load R. R loads in the folder where the workspace is saved and attempts to load the existing workspace. This workspace requires Package P which is not installed on Computer 2.

It seems that this is not valid for all packages.  Could you please tell what specific package is causing the problem?

---

### Post by SabreWolfy on 2011-03-01
> **jalvesaq said:**
> It seems that this is not valid for all packages.  Could you please tell what specific package is causing the problem?

I can't recall at the moment. If it is not a general problem, then please don't worry. If it happens again I'll post more details.

---

### Post by snesterko on 2011-03-11
> **jalvesaq said:**
> That's really strange! Do you have anything in ~/.vim/after/ftplugin/r.vim ?

Another test would be to make a backup of your .vim directory, delete the directory and then create a new one with just the Vim-R-plugin inside. Anyway, it seems that you are the only person experiencing this weird bug. Since I can't reproduce the bug, I can't be more helpful.

Thanks for trying to help me out. I found a solution to the autocommenting issue, what made this work was

```
autocmd FileType r setlocal formatoptions=croql
```

Maybe, someone else on a macvim would benefit from this. Have a nice day!

---

### Post by jalvesaq on 2011-11-25
I released an R package that I believe will interest most people subscribing to this thread: colorout (colorize R output in terminal emulators). The package is on CRAN and can be installed with the R command:
```
install.packages("colorout")
```
Once loaded, the output starts to get colorized, but you can also set the colors using a 256 colors scheme. Please, read the package help for details. Version 0.9-4 does not recognize hexadecimal numbers and does not use the value of getOption("OutDec"), but the next version will do.

---

### Post by bgc on 2012-05-15
Hi,

I recently made small changes to my vim setup, which for some reason means that now every time I try to start R from gVim, gVim freezes. It still works from vim. The only changes have been to switch to Vundle, and added a couple of (mostly unrelated) plugins. Do you have any clue why gVim might be crashing like that?

Thanks!

---

### Post by jalvesaq on 2012-05-15
> **bgc said:**
> I recently made small changes to my vim setup, which for some reason means that now every time I try to start R from gVim, gVim freezes. It still works from vim. The only changes have been to switch to Vundle, and added a couple of (mostly unrelated) plugins. Do you have any clue why gVim might be crashing like that?

Sorry, but I have no idea of what may be causing the problem. Does GVim freeze if you install the plugin outside Vundle?

---

### Post by bgc on 2012-05-15
No worries, thank you for your quick reply. It was working before I made these changes, so clearly it is something I did. I don't think it's vundle, after all I was using pathogen before that and that was fine, so maybe an issue with another plugin perhaps (e.g. powerline or latex-box). Thanks again.

---

### Post by bigmonty on 2012-11-06
I have followed all the instructions in the following site:

[http://www.lepem.ufc.br/jaa/r-plugin.html#r-plugin-installation](http://www.lepem.ufc.br/jaa/r-plugin.html#r-plugin-installation)


I am trying to install this on an ubuntu chroot running in an android phone. In terminal emulator when I type vim test.R  it says 
Tmux 1.5 or greater required. But my version is 1.6. Then I manually opened tmux, then vim test.R.  But none of the \rf or other commands work. 

Then in vim, I typed "ScreenShell  R". It opened R console right below in a split screen. Then I typed "ScreenSend" and it sent and executed R code in the console. I borrowed this command from another blog with only a vague idea about them.

Any idea what's going on here?

---

### Post by jalvesaq on 2012-11-06
> **bigmonty said:**
> Tmux 1.5 or greater required. But my version is 1.6. Then I manually opened tmux, then vim test.R.  But none of the \rf or other commands work.

What is the output of
```
tmux -V
```

It should be "tmux 1.6".

> **bigmonty said:**
> Then in vim, I typed "ScreenShell  R". It opened R console right below in a split screen. Then I typed "ScreenSend" and it sent and executed R code in the console. I borrowed this command from another blog with only a vague idea about them.

Any idea what's going on here?

ScreenSend is a command to send string to a application running in a Tmux pane started by ScreenShell. The Vim-R-plugin uses it send commands to R.

---

### Post by bigmonty on 2012-11-06
Thanks a lot for your quick response. I really appreciated that.

It is indeed tmux 1.6.  Let me elaborate a bit on the error code when I type  "vim test.R" in ubuntu console. 

Sorry, since it is in a mobile device, I can not copy and paste the whole error output: I am typing the whole thing, sorry if there is any typo.

Cannot execute shell /system/bin/sh
Error detected while processing /root/.vim/r-plugin/common_global.vim:line 2865

E484: Can't open file /tmp/vYco6Ye/0

Vim-R-plugin requires tmux>=1.5

But if I first open tmux and then type "vim test.R" in the console, the error message does not come. But none of the plugin command works. 

Any possible solution?

---

### Post by bigmonty on 2012-11-07
I am so much banking on you jalvesaq. Please help me out with this.

---

### Post by jalvesaq on 2012-11-07
> **bigmonty said:**
> Cannot execute shell /system/bin/sh
Error detected while processing /root/.vim/r-plugin/common_global.vim:line 2865

E484: Can't open file /tmp/vYco6Ye/0

Vim-R-plugin requires tmux>=1.5

You may edit ~/.vim/r-plugin/common_global.vim and DELETE the 11 lines of code that test Tmux version:

```
let s:tmuxversion = system("tmux -V")
let s:tmuxversion = substitute(s:tmuxversion, '.*tmux \([0-9]\.[0-9]\).*', '\1', '')
if strlen(s:tmuxversion) != 3
    let s:tmuxversion = "1.0"
endif
if g:vimrplugin_tmux && s:tmuxversion < "1.5"
    call RWarningMsgInp("Vim-R-plugin requires Tmux >= 1.5")
    let g:rplugin_failed = 1
    finish
endif
unlet s:tmuxversion
```

---

### Post by bigmonty on 2012-11-07
Thanks a lot, I will try to do that and let you know.

---

### Post by bigmonty on 2012-11-07
It spits out an error message very fast and goes to open test.R file after "vim test.R" command. Since it goes away very fast I can just see its the same kind of error message without 'tmux version warning.

---

### Post by jalvesaq on 2012-11-07
> **bigmonty said:**
> It spits out an error message very fast and goes to open test.R file after "vim test.R" command. Since it goes away very fast I can just see its the same kind of error message without 'tmux version warning.

In Vim, do the following in Normal mode to see past messages:

```
:messages
```

Note: it's better to start tmux first and, then, vim:

```
tmux
vim test.R
```

then you do \rf to start R.

---

### Post by bigmonty on 2012-11-07
Thanks again. I have been doing exactly that. First, tmux, then "vim test.R". Still it does not work.  It seems the plugin was not activated. \rf does not work.

---

### Post by jalvesaq on 2012-11-08
> **bigmonty said:**
> Thanks again. I have been doing exactly that. First, tmux, then "vim test.R". Still it does not work.  It seems the plugin was not activated. \rf does not work.

Did you follow the installation instructions and put these lines in your vimrc?

```
set nocompatible
syntax enable
filetype plugin on
filetype indent on
```

What's the output of 

```
set filetype
```

It should be "r".

---

### Post by bigmonty on 2012-11-12
Extremely sorry, could not reply earlier. The output is 

filetype=r

---

### Post by bigmonty on 2012-11-12
Extremely sorry, could not reply earlier. The output is 

filetype=r

I have also put those lines on vimrc.

---

### Post by jalvesaq on 2012-11-12
> **bigmonty said:**
> Extremely sorry, could not reply earlier. The output is 

filetype=r

I have also put those lines on vimrc.

Sorry, but I don't know what more can be done to discover what's causing the problem. I guess that it's something in your .vimrc, your .vim directory, or our .tmuxconf...

---

### Post by bigmonty on 2012-11-19
Its all right. Thanks for helping me this far.

---

### Post by bgc on 2013-02-22
Apologies for the somewhat tangential question, but this is something that I have been wondering for a bit now. In the terminal, I have set vi keybindings. When I'm within tmux+vim+R, if I switch the R command prompt, the vi keybindings are no longer available (e.g., switching to normal mode to navigate a command that I entered). Does anyone know if there's a way of making vi keybindings available from within the R command prompt?

Thanks!

---

### Post by jalvesaq on 2013-02-22
> **bgc said:**
> Apologies for the somewhat tangential question, but this is something that I have been wondering for a bit now. In the terminal, I have set vi keybindings. When I'm within tmux+vim+R, if I switch the R command prompt, the vi keybindings are no longer available (e.g., switching to normal mode to navigate a command that I entered). Does anyone know if there's a way of making vi keybindings available from within the R command prompt?

What about editing ~/.inputrc as suggested here:

[http://stackoverflow.com/questions/6235034/vi-keybindings-for-r-command-line-like-in-bash](http://stackoverflow.com/questions/6235034/vi-keybindings-for-r-command-line-like-in-bash)

---

### Post by bgc on 2013-02-22
Thanks for that! I did google it but didn't see that post.. Perhaps I should improve my googling skills..

---

