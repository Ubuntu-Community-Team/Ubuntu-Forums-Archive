---
title: "Edit the sudoers file"
date: 2009-04-15
forum: General Help
---

### Post by Ticketoride on 2009-04-15
I am trying to edit this File, but it won't go through per the Instructions on another Website below:

========================================================================

Edit the sudoers file

Open a Terminal window. Type in sudo visudo. Add the following lines to the END of the file (if not at the end it can be nullified by later entries):

<username> ALL=NOPASSWD: ALL

Replace <username> with your user name (without the <>). This is assuming that Ubuntu has created a group with the same name as your user name, which is typical. You can alternately use the group users or any other such group you are in. Just make sure you are in that group. This can be checked by going to System->Administration->Users and Groups

Example:

michael ALL=NOPASSWD: ALL

Type in x to exit. This should prompt for an option to save the file, type in Y to save.

Log out, log back in. This should now allow you to run the sudo command without being prompted for a password. 

==========================================================================

When I type x, it won't exit, nor produce any Option to save the file.

What is the correct Way of saving Changes?

---

### Post by Nepherte on 2009-04-15
First press the esc key and then type:
```
:wq
```

---

### Post by utnubuuser on 2009-04-15
Hi -- Couldn't say about using VI, (could never get it to work either), but I've edited the sudoers file with nano and it seems to be ok.
ctrl+x to save.

---

### Post by Nepherte on 2009-04-15
For the record: the key combinations you mentioned are indeed referring to the text editor nano, which might be a lot easier for you to work with.

To edit the sudoers file with nano instead of vi, use:
```
sudo EDITOR=nano visudo
```

---

### Post by Ticketoride on 2009-04-15
> **utnubuuser said:**
> ctrl+x to save.
It does not save the File, but brings up this Prompt, 

**Save modified buffer (ANSWERING "No" WILL DESTROY CHANGES) ?**

I type **Y**, then hit **Enter**, but the GNU nano 2.0.9 just sits there waiting for me to do what?

If I the close the Window off, I am met with a Dialog giving me 2 Choices: Either **Cancel** the Changes or **Close Terminal**, neither one saving the Changes to the File.

There is a Step missing between hitting **Y** to save the Changes and closing off the Terminal Window.

> **Nepherte said:**
> First press the esc key and then type:
```
:wq
```
I hit the **ESC** Key, then typed In ---> **:wq** and all that did was add that to the File and shows as: 

**Micheal ALL=NOPASSWD: ALLwq**

The File would not take the colon either.

> **Nepherte said:**
> To edit the sudoers file with nano instead of vi, use:
```
sudo EDITOR=nano visudo
```

Whether I use:

1. sudo EDITOR=nano visudo
2. sudo gedit=nano visudo
3. sudo visudo

... all do the same thing and launch GNU nano 2.0.9 in Jaunty 9.04.

**sudo gedit visudo** only launches a blank Page.

---

