---
title: "Strange behaviour of vi"
date: 2010-05-06
forum: Desktop Environments
---

### Post by sdp0et on 2010-05-06
I am using the standard terminal started with Applications->Accessories->Terminal.

When I open vi, I am experiencing strange behaviour.  If it is a new file, the character sequence "[=0C" is before the cursor.  It is not "in" vi, as the line cannot be deleted nor the characters removed.  If I switch to input mode, there is no notification at the bottom of the screen like I'm used to, and the same character sequence is interjected intermittently between the characters I type.  Backspace and Ctrl-h do not work, so I cannot delete individual characters, but when I use 'dd' to delete a line, the line does disappear and the "[=0C" on the line above it turns blue.  In edit mode, the directional arrows write letters instead of moving, and even with "set term=cons25" allows up and down to work, but left and right are ignored.


If I open an existing file, the character sequence overwrites (really displays over) the first few characters of the file, with the same behaviour for adding new text.  When I cat the file, it is normal. 

I have also tried other terminals (all VTE based) with the same problems.

I really only use the gui (gnome) for web browsing and as a convenient organizer for multiple terminal sessions, so I'm not very familiar with desktop settings.  

I'd appreciate any help. 

paul

edit: This is a fresh (this morning) install of 10.4 standard.  I have installed tomcat6 with apt-get, and noticed this while trying to edit config files for the server.  Other than this and using Ubuntu software center to install additional terminals, everything is as defaulted during installation.

---

### Post by davewill on 2010-05-06
sudo apt-get install vim

should give you the expected results

---

### Post by sdp0et on 2010-05-06
thanks for the reply.  It went through an install, but the new version does pretty much the same thing, but is different enough to help isolate symptoms:

Since vi doesn't seem to be aware of the weird characters, I think that this part is not a problem with vi but the desktop or terminal.

The difference now is that it looks like the sequence "[=0C" is drawn along with and before the cursor.  The left and right arrows work, and if I press the right arrow anumber of times to move along a line with text on it I get "[=0C" and if I move back left "[=0CCCCCCCCCCCCCCCCCCCCCC".  this even shows up in the command section, so ":wq" looks like ":[=0Cw[=0Cq[=0C" and the sequence is not written to the file along with changes I make.

---

### Post by davewill on 2010-05-06
take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=445626](http://ubuntuforums.org/showthread.php?t=445626)

---

### Post by davewill on 2010-05-06
Oh, and just to make sure, you did type:

vim <filename to edit>
instead of
vi <filename to edit>
?

---

### Post by sdp0et on 2010-05-06
I believe that vi has just redirected to vim for the longest time on most standard installations.  But I did try both just in case. 

I looked at that thread.  The solution was creating a .vimrc file.  after first experiencing this problem, I copied my .vimrc from an old installation but that didn't work.

---

### Post by sdp0et on 2010-05-06
I fatfingered the file copy.  renaming the file to ".vimrc" seems to have fixed the issue.  Thanks for the guidance.

---

