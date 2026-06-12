---
title: "Kate and KWrite in Oneiric -- cannot specify filename to save as"
date: 2011-12-24
forum: Desktop Environments
---

### Post by jamadagni on 2011-12-24
Since updating to Oneiric, I have been unable to specify a file name for Save As in Kate and KWrite. Simply put the keyboard doesn't work in the Save As dialog at all, not even the Enter key.

The workaround I have been using is to create an empty file from the terminal in the required folder and then navigating to the required folder using the mouse, then selecting the empty file using the mouse, clicking on Save, and then saying Yes when it asks whether to overwrite.

This is quite irritating. Can anyone please provide a solution? I never had this problem till Natty.

---

### Post by oldos2er on 2011-12-24
That's odd. In Kate, if you hit Ctrl-s, you should see a file dialog with the cursor in the empty 'Name' field; does this work for you?

Which version of Kate are you running?

---

### Post by jamadagni on 2011-12-25
Thanks for replying. I'm running Kate 3.7.2 on KDE 4.7.2 on Kubuntu Oneiric and I am still experiencing this problem.

BTW unless it is a new document, hitting Ctrl+S will not turn up the Save As dialog.

---

### Post by idef1x on 2011-12-28
Ctrl-S is normaly for saving the current document, so sounds logical that save as won't show up.
If your editing an existing file and want to save it under a new name, why not select "Save As..." from the File menu? Or am I missing your point?

---

### Post by jamadagni on 2011-12-28
Please read my OP. The dialog shows up all fine, but I am unable to type in the desired location and filename of the file to save.

---

### Post by idef1x on 2011-12-29
Ah sorry read it too fast i guess. Hmm weird problem you have...don't have it myself. You might try to upgrade to 4.7.4? This version solved a lot of bugs according to some people. Might be worth a shot?

---

### Post by jamadagni on 2011-12-29
As per [http://www.kubuntu.org/kde-sc-474](http://www.kubuntu.org/kde-sc-474) the 4.7.4 updates are still in the PPA and not main repository. The repo contains 4:4.7.3-0ubuntu0.1 to which I have now upgraded. But I still have this problem. :(

I tried using some other KDE apps and saving files from them but I never have any trouble there -- only with Kate and KWrite. :( Shall I try deleting the katerc or something and try again?

---

### Post by jamadagni on 2011-12-29
I now tried deleting ~/.kde/share/config/katerc|kwriterc and opening Kate/KWrite. Problem persists. :(

---

### Post by idef1x on 2011-12-30
To see if it has to do with your user profile, you can create an other user, log out, log in as that newly created user and try again?

If something is in a PPA doesn't mean it's unstable or so. With this PPA you just get the last stable updates.

---

### Post by SeijiSensei on 2011-12-30
I'll ask a stupid question.  Are you sure you have write privileges in the directory where you're trying to save the files?  If you run "touch /path/to/the/directory/testfile" do you get a permission denied error?

---

### Post by jamadagni on 2012-01-07
@SeijiSensei: Actually the method I have been using to save files in Kate/KWrite for now is to open a terminal, go to the required directory, create an empty file using touch, and overwriting that by clicking on it in the Kate/KWrite dialog box.

@idef1x: I'll try that and get back as soon as I can.

---

### Post by jamadagni on 2012-01-07
@SeijiSensei: Actually the method I have been using to save files in Kate/KWrite for now is to open a terminal, go to the required directory, create an empty file using touch, and overwriting that by clicking on it in the Kate/KWrite dialog box.

@idef1x: I'll try that and get back as soon as I can.

---

