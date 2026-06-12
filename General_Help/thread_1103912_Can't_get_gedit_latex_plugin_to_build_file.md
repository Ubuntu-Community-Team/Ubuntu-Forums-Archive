---
title: "Can't get gedit latex plugin to build file"
date: 2009-03-23
forum: General Help
---

### Post by nortexoid on 2009-03-23
I'm using Ubuntu 8.10 (wubi) and gedit with the latex plugin, which seems to be working in all respects except for building the file. When I click the Tools-->LaTeX->PDF it doesn't do anything. (This is the same for all build options, e.g. to PS, etc.) I have texlive installed and can build from command line.

I imagine the build parameters are not set correctly in the plugin configuration. How do I do this?

---

### Post by hugmenot on 2009-03-23
Did you install the »rubber« package as well?

There is an error log in the bottom panel. Perhaps you should activate it in the View menu.

---

### Post by nortexoid on 2009-03-23
> **hugmenot said:**
> Did you install the »rubber« package as well?

There is an error log in the bottom panel. Perhaps you should activate it in the View menu.

I just installed rubber but it has no affect on the build process. The bottom pane just tells me the parameters specified in the plugin configuration for pdflatex. I imagine that's where it outputs the build info (as in the command line)?

---

### Post by hugmenot on 2009-03-23
Yes, it should output if somethign goes wrong.

Can you open a terminal and try out rubber on your file without gedit?

```
rubber -sdf file.tex
```

---

### Post by nortexoid on 2009-03-24
> **hugmenot said:**
> Yes, it should output if somethign goes wrong.

Can you open a terminal and try out rubber on your file without gedit?

```
rubber -sdf file.tex
```

Yeah that worked--it built the file. For some reason it doesn't execute the command when I ask it to do so from the GUI in gedit. I don't see how, but could this be caused by being an wubi installation?

---

### Post by nortexoid on 2009-03-25
Nobody with the same issue, or better, a solution? Unfortunate, as the plugin "half" works. It looks like building from the command line for me.

---

### Post by hugmenot on 2009-03-25
Try to re-use the exact command line from the plugin&#8217;s profile settings on the terminal and see if it still works.

I can&#8217;t test anything myself, because the plugin doesn&#8217;t load at all in Jaunty.

---

### Post by nortexoid on 2009-03-25
The command works when I replace the placeholder $filename with the actual file name.

It appears that the command is not being issued at all when selected from the GUI. I wonder why. I can even add other commands that do nothing as well. This isn't looking promising...

---

### Post by hugmenot on 2009-03-25
Try to run gedit from terminal and inspect the output that appears on the shell when you start a task.

---

### Post by nortexoid on 2009-03-25
Following your suggestion I get the following:

```
Traceback (most recent call last):
  File "/usr/lib/gedit-2/plugins/GeditLaTeXPlugin/src/base/decorators.py", line 271, in _on_action_activated
    action.activate(self._window_context)
  File "/usr/lib/gedit-2/plugins/GeditLaTeXPlugin/src/tools/__init__.py", line 124, in activate
    self._runner.run(context.active_editor.file, self._tool, tool_view)
  File "/usr/lib/gedit-2/plugins/GeditLaTeXPlugin/src/tools/__init__.py", line 162, in run
    chdir(file.dirname)
OSError: [Errno 2] No such file or directory: '/host/Documents%20and%20Settings/Owner/My%20Documents/Graduate%20Studies/Work%20in%20progress'
```

I suppose the last line is telling. Is the problem spaces in my directory and file names? (They were made from my Windows XP partition.) I wonder how this might be fixed.

On another note, I notice automatic code completion doesn't work either. I have to manually trigger the completion list using Ctrl + Space. (This doesn't bother me much.)

---

### Post by hugmenot on 2009-03-26
I guess it is the spaces in the file name.

But [according to the bugtracker]("http://sourceforge.net/tracker/?limit=10&func=&group_id=204144&atid=988428&assignee=&status=&category=&artgroup=&keyword=&submitter=&artifact_id=&limitz=10&assignee=&status=&category=&artgroup=&submitter=&keyword=spaces&artifact_id=&submit=Filter&limitz=10") all bugs pertaining to spaces in the filename have been fixed.

So, dunno. Do you have the latest version?

---

### Post by nortexoid on 2009-03-27
I have the latest version. In fact I tried installing older versions as well that didn't work. I think it's time to give up. It was worth a try!

---

### Post by hugmenot on 2009-03-28
What you can always do, as a workaround, just create a symlink!

Like this:

```
ln -s "/host/Documents and Settings/Owner/My Documents/Graduate Studies/Work in progress" $HOME/Desktop/wip
```

This way your spaces won&#8217;t matter a bit.

---

### Post by nortexoid on 2009-03-29
I tried putting a tex file that had no spaces in its name in a folder also without spaces in its name, and the plugin *still* didn't work. So apparently it has nothing to do with spaces. It's something deeper, more elusive, infinitely perplexing.

I've come to live with building from the command line. But thanks for all your help with this mess.

---

### Post by infestor on 2009-05-27
I have the same problem like [nortexoid]("http://ubuntuforums.org/member.php?u=796424"). i got the *gedit latex plugin* build pdf only once -by chance-, and that was that; now the plugin cannot build anything!
Is it because the damn plugin is outdated for jaunty?

---

### Post by hugmenot on 2009-05-28
Yes, that may be.

If you feel comfortable with the shell, then with a few commands you could install the most recent revision from the subversion repository. I looks like the spaces issue was fixed since the release that is in Jaunty.

This is how I would do it:
```

sudo apt-get remove gedit-latex-plugin
cd /tmp
svn co https://gedit-latex.svn.sourceforge.net/svnroot/gedit-latex/GeditLaTeXPlugin/trunk/ GeditLaTeXPlugin
cd GeditLaTeXPlugin
sh install.sh

```

See if removing the «gedit-latex-plugin» package also removes «rubber». You will need it.

---

### Post by nortexoid on 2009-05-28
> **hugmenot said:**
> Yes, that may be.

If you feel comfortable with the shell, then with a few commands you could install the most recent revision from the subversion repository. I looks like the spaces issue was fixed since the release that is in Jaunty.

This is how I would do it:
```

sudo apt-get remove gedit-latex-plugin
cd /tmp
svn co https://gedit-latex.svn.sourceforge.net/svnroot/gedit-latex/GeditLaTeXPlugin/trunk/ GeditLaTeXPlugin
cd GeditLaTeXPlugin
sh install.sh

```

See if removing the «gedit-latex-plugin» package also removes «rubber». You will need it.

Brilliant! It finally works. The version I installed from the repos broke the show/hide tabbar plugin, it never compiled, and code completion would only be activated by pressing ctrl + space.

I am sincerely grateful--thanks.

---

### Post by infestor on 2009-05-29
> **hugmenot said:**
> Yes, that may be.

If you feel comfortable with the shell, then with a few commands you could install the most recent revision from the subversion repository. I looks like the spaces issue was fixed since the release that is in Jaunty.

This is how I would do it:
```

sudo apt-get remove gedit-latex-plugin
cd /tmp
svn co https://gedit-latex.svn.sourceforge.net/svnroot/gedit-latex/GeditLaTeXPlugin/trunk/ GeditLaTeXPlugin
cd GeditLaTeXPlugin
sh install.sh

```See if removing the «gedit-latex-plugin» package also removes «rubber». You will need it.

My problem still persists :(

---

### Post by hugmenot on 2009-05-29
Eto, when you start gedit from a terminal and then use the build command, what is the output printed on the terminal?

Please try the things that I had suggested above to get to the bottom of this.

---

### Post by infestor on 2009-06-01
> **hugmenot said:**
> Eto, when you start gedit from a terminal and then use the build command, what is the output printed on the terminal?

Please try the things that I had suggested above to get to the bottom of this.

what build command?  (yes, i did try your suggestion but didnt work out for me :()

---

### Post by hugmenot on 2009-06-01
Uzhas.

Ok. Start Gedit from command line. Open your .tex file. Does the plugin load? You should see output pertaining to loading the plugin in the terminal window. Ok?
Now open the Tools menu and click on »LateX &#8594; PDF«. What happens.  Open the Bottom Panel in the View Menu and look for clues.

And what gets printed in the terminal window. Paste the output here.

That should help to figure it out.

---

### Post by infestor on 2009-06-02
> **hugmenot said:**
> Uzhas.

Ok. Start Gedit from command line. Open your .tex file. Does the plugin load? You should see output pertaining to loading the plugin in the terminal window. Ok?
Now open the Tools menu and click on »LateX &#8594; PDF«. What happens.  Open the Bottom Panel in the View Menu and look for clues.

And what gets printed in the terminal window. Paste the output here.

That should help to figure it out.

yes, the plugin loads. 

"bottom panel" shows that i dont have rubber installed. also  when i tried <<sh install.sh>> command i got a <<permission denied>> error. sudo doesnt overcome this. here is the output: [http://pastebin.com/f409b5c03](http://pastebin.com/f409b5c03)

---

### Post by hugmenot on 2009-06-02
> **infestor said:**
> yes, the plugin loads. 

"bottom panel" shows that i dont have rubber installed. 

Ok, that makes sense. You need the rubber package for making a document. Just install that package and retry.

> 
also  when i tried <<sh install.sh>> command i got a <<permission denied>> error. sudo doesnt overcome this. here is the output: [http://pastebin.com/f409b5c03](http://pastebin.com/f409b5c03)

What is th exact output here?

---

### Post by infestor on 2009-06-02
OK the problem was that I lacked <<rubber>>. I installed it and the plugin  works now. Probably it was removed along with the latex plugin.
[hugmenot]("http://ubuntuforums.org/member.php?u=80407"), thanks a lot for your help, a lot! :D

---

### Post by federa on 2009-06-19
hi!!
if someone still have problems with gedit latex plugins, it's possible to solve it with these few steps:
1) tools - external tools
2) create new one (you could call it "latex building")
3) choose your favourite keybord shortcut (i've choosen "shift+alt+ctrl+b")
4) in the command space type the following instruction: pdflatex "$filename"
5) in the input menu select "current document"
6) output menu "display in bottom pane"
7) applicability "all documents"

let's latex some files now!!!!

:D

---

### Post by Chninkel on 2009-09-04
Hi

I had the same problem (using Jaunty) : Tools --> Latex-->PDF : nothing

using command line I had a warning about "command ctags not found".

installed package exuberant-ctags. problem solved ! it creates and opens the pdf file :D

Last little thing : auto-completion needs to be triggered using ctrl+space. But actually I prefer it that way :P

---

