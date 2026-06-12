---
title: "Uninstalled Wine; but how do I get rid of the Windows programs?"
date: 2009-04-19
forum: General Help
---

### Post by funky_uncle on 2009-04-19
I installed a few windows program under Wine (like Mediamonkey and Quicktime, they didn't work btw). Quicktime has the option of uninstalling, which I did, but it's still there, apparently. So I uninstalled Wine altogether (from Synaptic). However, it still sits under my applications meny, and Mediamonkey and Quicktime still appear there.

So... how do I get rid of the whole caboodle? I'm cautios to snoop around in my root folders deleting files unless I know for sure I'm deleting the right ones.

---

### Post by Titan8990 on 2009-04-19
The thing about uninstallation of packages is that it never touches a user's home directory where things such as these menu options would reside. If you right click on the menu you should be able to select the menu editor to remove the options from the menu. 

To delete all associate files with wine, delete the following folder:

~/.wine

In command form:

```
rm -rf ~/.wine
```

---

### Post by 67GTA on 2009-04-19
After removing the .wine folder as Titan8990 suggested, go to > /home/yourusername/.config/menus/applications-merged and delete any program entries for wine there. This will clean them out of your menu.

---

### Post by funky_uncle on 2009-04-19
Thanks!
> **Titan8990 said:**
> To delete all associate files with wine, delete the following folder:

~/.wine

In command form:

```
rm -rf ~/.wine
```It worked! Though i don't know how... what does the "~" do?

---

### Post by Vaphell on 2009-04-19
~ = /home/yourname/

so ~/.wine = /home/yourname/.wine

---

### Post by Titan8990 on 2009-04-19
~ means the home directory of the current user. So you always know where to find your home :D.

You can get it to print out what it represents with:


echo ~

---

### Post by funky_uncle on 2009-04-19
Brilliant :)

Just one last thing - I've forgotten how to add "[SOLVED]" to the thread title. Tried editing the OP in advanced mode, but it doesn't seem to work.

---

### Post by Titan8990 on 2009-04-19
Thread tools menu above the first post. Last time I was around the forums, marking posts as solved was broken.

---

