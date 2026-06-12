---
title: "SVN1 - simple version control for your thesis or other 1 person project"
date: 2007-01-04
forum: Education &amp; Science
---

### Post by Steveire on 2007-01-04
I'm using version control for my thesis and related python code that I'm writing, and I've started using it for everything. I wrote a simple script to keep a window open with the diff, so that after a save I can see the diff, write a summary message and commit.

You should probably learn something about some svn commands before using this script, and certainly read through the code to see what it does.

Copy the code to svntool.py and chmod a+x the file. then 
```

sudo mv svntool.py /usr/local/bin/

```
To use it, cd into a working copy from an svn repo, and run svntool.py.
Then start Kile/gedit/whatever make some edits, save them, view the diff, make a comment, and commit it. also try adding and removing files (from directories already listed in the repo).

GPL, no warranty, own risk etc.

Features:
[list]
[*] Keeps a list of all files in the repo.
[*] Displays files which are not already in the repo.
[*] Easily add and remove files from the repo.
[/list]

Bugs(features):
[list]
[*] Does not display newly created directories for addition to the repo. This is deliberate because it would add all files in the directory whether the user wanted them all or not. v0.2 will display files in the directory as candidates for inclusion.
[*] Doesn't display any errors, for example if the current directory is not a working copy, if you've left the message field blank. v0.2 will have a 'console' built in to display the output of the svn commands.
[/list]

```

#!/usr/bin/env python
#-*- coding: utf-8 -*-
# svntool.py v0.1

import os, thread, time
from Tkinter import *

class SvnTool(Tk):
  def __init__(self):
    Tk.__init__(self)
    self.title("Svn Tool - " + os.getcwd())
    leftFrame = Frame(self)
    leftFrame.pack(side=LEFT)
    rightFrame = Frame(self)
    rightFrame.pack(side=RIGHT)

    self.message = Text(leftFrame, height=5)
    self.message.pack()
    buttonFrame = Frame(leftFrame)
    buttonFrame.pack()
    commitButton = Button(buttonFrame, text="Commit",
        command=self.commit)
    commitButton.pack(side=LEFT)
    self.diff = Text(leftFrame)
    self.diff.pack()

    label = Label(rightFrame, text="Available files")
    label.pack()
    self.filesList = Listbox(rightFrame, width=50)
    self.filesList.pack()
    rightButtonFrame = Frame(rightFrame)
    rightButtonFrame.pack()
    fileAdd = Button(rightButtonFrame, text="Add",
        command=self.addFile)
    fileAdd.pack(side=LEFT)
    fileRemove = Button(rightButtonFrame, text="Remove",
        command=self.removeFile)
    fileRemove.pack(side=LEFT)
    thread.start_new_thread(self.fresh, ())

  def addFile(self):
    file = self.filesList.get(ANCHOR)
    if file.startswith("?"):
      os.system("svn add " + file[2:])
    elif file.startswith("A"):
      pass
    elif file.startswith("D"):
      os.system("svn revert " + file[2:])
  
  def removeFile(self):
    file = self.filesList.get(ANCHOR)
    if file.startswith("A"):
      os.system("svn revert " + file[2:])
    elif file.startswith("D"):
      pass
    elif not file.startswith("?"):
      os.system("svn rm " + file)
      self.filesList.insert(ANCHOR, "? " + file)
      self.filesList.delete(ANCHOR)

  def commit(self):
    if self.message.get(0.0, END).strip() is not '':
        os.system("svn commit --message=\"" +
            self.message.get(0.0, END)[:-1] + "\"")
        self.message.delete(0.0, END)
  
  def fresh(self):
    while True:
      files = []
      fileslist = os.popen2("svn status -v")[1].readlines()
      for file in fileslist:
        if not os.path.isdir(file[40:-1]):
          if file.startswith("?"):
            files.append("? " + file[40:-1])
          elif file.startswith("D"):
            files.append("D " + file[40:-1])
          elif file.startswith("A"):
            files.append("A " + file[40:-1])
          else:
            files.append(file[40:-1])
      if files != list(self.filesList.get(0, END)):
        self.filesList.delete(0, END)
        self.filesList.insert(END, *files)      

      diffText = os.popen2("svn diff")[1].read()
      if diffText != self.diff.get(0.0, END)[:-1]:
          self.diff.delete(0.0, END)
          self.diff.insert(END, diffText)
      time.sleep(1)

if __name__ == "__main__":
  root = SvnTool()
  root.mainloop()

```

---

