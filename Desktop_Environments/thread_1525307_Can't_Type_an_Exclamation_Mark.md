---
title: "Can't Type an Exclamation Mark"
date: 2010-07-06
forum: Desktop Environments
---

### Post by wingman358 on 2010-07-06
I can't type an exclamation mark with my keyboard. I can type other symbols that require the shift key (~ @ # $, etc) but Shift + 1 does not give an exclamation point.

Here's the intriguing part: following a tip from another thread, **I changed my Visual Effects setting **(System > Preferences > Appearance > Visual Effects tab)** from **the default **"Normal" to **the setting** "None". Immediately after doing this, I was able to type exclamation points.** Problem solved, right? Not quite.

After discovering the solution, I decided it would be a _great_ idea to experiment to *make sure* the Visual Effects setting was really the culprit. So I flipped my Visual Effects back to the default "Normal", and sure enough, I stopped being able to type exclamation marks.

Having verified the (apparent) cause of the issue, I tried my solution of changing the Visual Effects to "None". Of course the "solution" didn't work this time :-| (so much for my _great_ idea) and I am left unable to type an exclamation point.

I have concluded that the fault must lie within my user's configuration **(I can type as many exclamations as I want when logged in as other users).**

---

### Post by Yarui on 2010-07-06
If you think it's something going on with your user account, you could try renaming your home folder from your name to something else temporarily.  That way the next time you log in none of your config files will be loaded.  If this fixes the problem you will know that it has something to do with your config files in your home folder.  You could then try to narrow it down by testing out your config files in the same way one by one, if you have the patience for that.

---

### Post by wingman358 on 2010-07-06
> **Yarui said:**
> If you think it's something going on with your user account, you could try renaming your home folder from your name to something else temporarily.  That way the next time you log in none of your config files will be loaded.  If this fixes the problem you will know that it has something to do with your config files in your home folder.  You could then try to narrow it down by testing out your config files in the same way one by one, if you have the patience for that.
That's actually a brilliant idea. I'm kind of new to this. Do you have any clue which config files that might be to blame? That would give me something to start with.

---

### Post by Yarui on 2010-07-06
I don't have the slightest idea.  I would just start by changing the name of your /home/username directory to /home/somethingelse then restart and see what happens.  If that fixes it change it back and try testing out your config files. You can find all the config files in your home folder with
```
ls -a ~
```
The files and folders that start with a . are all hidden configuration files/folders.  You can try to decide which one you think is doing it and test that one, or maybe you would find it easiest to test one half of them first, then the other half.  That would narrow it down to half of your files, continue with half of the half you have narrowed it down to and so on.

To test out the files I would just make a new folder called "testing" or something and move the config files in question into that folder.  If the problem is fixed while they are in that folder then you know that one of those files is to blame.

---

### Post by wingman358 on 2010-07-06
I did the above method suggested by Yarui and narrowed it down to  .gconf/apps/. I  remembered editing something in there,  so I ran

 ```

$ gconf-editor 

```

Then I remembered I was in /apps/metacity/global_keybindings  recently, so I brought that directory up and looked for  "<Shift>1", which I immediately found as run_command_1. I disabled  the keybinding by replacing the text "<Shift>1" with "disabled". I  then hopped over to the corresponding file at  /apps/metacity/keybinding_commands and erased the command I wrote in for  command_1.

Now I've got my !! back [IMG]http://c0491962.cdn.cloudfiles.rackspacecloud.com/images/questions/images/smilies/biggrin.gif[/IMG]

---

