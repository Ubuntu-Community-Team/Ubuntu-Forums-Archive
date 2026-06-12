---
title: "Gnome / Nautilus annoyances"
date: 2008-08-09
forum: Desktop Environments
---

### Post by Zakhafr on 2008-08-09
Hello community,

I have a lot of ergonomics annoyances with Gnome / Nautilus.
Before posting them as bugs to launchpad, I post here in case there is some customizing I didn't find.

_-1) Nautilus: impossible to "Paste" when windows of a directory is full._
Let's say I want to copy some files. I go to the source directory, select file(s), then right click + Copy.
Then I go to destination directory, and I want to paste with the same mouse manipulation.
Well, if the right pane showing the objects in the directory is "not full", you just click in an "empty space", and that's done.
If you use mode "list", and the right pane is "full", eg. the vertical slidebar appears, there is simply no way to do this manipulation because you have no "empty space".
If you put the cursor on a file, right click will not give you the option to paste in that directory.

Of course alternate ways still work : CTRL+V or pasting through the main menu of Nautilus.

**Severity **: annoying.


_-2) Nautilus: no good solution for text/script files._
There is an option to set the default: edit a text, or launch it (supposing it is a script), or ask.
These options seem to be redundant. I'm wondering why a file having Type MIME: application/x-shellscript, and/or extension **.sh** isn't launched by default, and a file having Type MIME: text/plain and/or extension **.txt** is not displayed in the editor.
So if you set one of the options: edit or launch... it's always wrong!
I still didn't find the command to launch a .sh in a terminal (and see the result) but there is also another issue. This issue is when you work with files on FAT32 or NTFS. That's what I have to do because I share developement files with Windows. On these types of non-Unix file system, you cannot set permission to execute.

So, the only remaining option working is: ask everytime.
And that's very boring to have to click twice to open a text file or launch a shell script.
Even more... if I don't clck quick enough, a stupid windows nags me intructing to click cancel if I want to cancel! After 25 years working with computers I should know that :-p

If I remember well KDE does better, by default you edit, if you want to launch you do CTRL-E (Execute) on the file.

But really, what would make sense is:
txt/plain or .txt files defaulted to edit
application/x-shellscript or .sh files defaulted to launch.

Ergonomics is about doing automatically what you will probably want 90% of the time. And for the 10% remaining, if I want to edit a .sh file, I'm fine with right-clicking on it and choosing editor (and it should NOT be defaulted to editor for next click!)

**Severity**: annoying


_-3) Gnome-Nautilus: single click inconsistency._
Except if I missed a setting (or if it is ridiculously positionned as it is in KDE under the mouse preference), I can activate "Single click" in Nautilus, but the standard system dialog boxes to choose a file/directory keep a "double-click" behaviour.
And I don't mean trying to use KDE programs on Gnome!
Just try going to "single click" in Nautilus.
Then open, let's say: Totem and choose a file, you'll have to "double-click" to do so.

**Severity**: inconsistency


_-4) Nautilus: single click doesn't "select" objects, resulting in not ergonomic behaviour._
When Nautilus is set to "single-click", multiselection becomes not very natural.
That is because objects under mouse cursor are underlined, but do not get focus/selection.
So to multi-select, you must first Shift-Click or Ctrl-Click on the first element of your list.

Keyboard shortcuts, such as F2 to rename, apply to the object having the focus. So with single-click, they do not apply to the element underlined unless you give it focus/select. Of course clicking would give focus to the element... but would also launch it, which you do not want. So workaround could be to Shift-Click (gives focus/selects but do not launch) before using the shortcut.
This is really bad ergonomics! 

**Severity**: bad design (ergonomics)



I know Ubuntu wants to be able to compete with Macintosh ergonomics, so I hope these basics things will be fixed... because at the moment, my feeling is that there is way to go!

*Keep up the good job!*

---

### Post by svivian on 2008-08-09
I'm with you on #1. I use right-click for creating a new folder since it's the quickest way. A temporary workaround is to make the columns in List View not stretch across the whole window, then there is a space at the right to right-click.

#4 on your list reminded me, there is a problem when using Ctrl-Shift-click in Nautilus. Example:
- Assume you have a bunch of files "file1", "file2", ...etc.
- Click a file (eg "file1").
- Shift-click to select multiple files (eg click "file3" and get files 1-3 all selected).
- Ctrl-click another file (eg "file6").
- Ctrl-Shift-click another file (eg "file8").
You should have had files 1-3 and 6-8 (6 files total) all selected, "file7" isn't selected.

*Is there any blog or other site to learn of work activity etc on Nautilus?* (I'm aware of bugzilla)

---

### Post by Zakhafr on 2008-08-09
> **svivian said:**
> I'm with you on #1. I use right-click for creating a new folder since it's the quickest way. A temporary workaround is to make the columns in List View not stretch across the whole window, then there is a space at the right to right-click.


Yes, good workaround.
But what does it cost to display "Paste" on the right click menu, and allow copying in the currently browsed directory even if the cursor is on some object!

*Keep up the good job !*

---

### Post by satish_j on 2009-07-17
agree with you...point no 1 is really very annoying..
has anyone got the solution for this??
Thing is,when you click any file/folder,nautilus allocates the entire row to this file/folder..so right-clicking on it will definitely give the options of selected file/folder.
There should be some blank space between the name,size,modifiedtime,etc.. so that right-clicking in this blank space produces the same menu as the menu produced while right-clicking on desktop.
May be some patch for nautilus can do this trick..

---

### Post by provoko on 2010-11-05
Has anyone found a way to turn off single clicking on empty space selects whole line?

---

### Post by satish_j on 2010-11-08
In Lucid,there is this new compact view mode which is,in a way,a workaround for this issue.List view mode still has the same problem.

---

