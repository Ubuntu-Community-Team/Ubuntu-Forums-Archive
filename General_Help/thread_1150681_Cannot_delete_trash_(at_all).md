---
title: "Cannot delete trash (at all)"
date: 2009-05-06
forum: General Help
---

### Post by HandleWithCare on 2009-05-06
On my desktop (running ubuntu 9.04) I cannot empty trash. I hear you think, yet another one, read the forum and do 
```
sudo rm -rf ~/.local/share/Trash/files/*
```
Well, that doesn't work. I don't get any permission errors when I try to delete as well. 
The weird thing is, there are several file is trash, I can even open them from there, but when I go to ~/.local/share/Trash/files nothing is there. When I hit empty trash nothing happens. When I select a file and choose delete permanently from the context menu I get:
```

Error while deleting.
There was an error deleting [some file I try to delete]

```
And when I click on show more details it says:
```
Failed to delete the item from the trash
```
I'm really stuck here, hope someone can help

---

### Post by BslBryan on 2009-05-06
Hello!

I think we all have this problem on occasion.

Just delete the files folder and see what happens. 

Good luck. :-)

---

### Post by HandleWithCare on 2009-05-06
does nothing I'm afraid... The files remain in the trash...

---

### Post by StormRoBoT2 on 2009-05-06
is the file from ur portal hard disk? or ur pendrive?

---

### Post by BslBryan on 2009-05-06
Hmmm....  :-k

How about trying the same procedure in nautilus?

So, Alt+F2, then
```
gksu nautilus
```
Then, navigate to your home directory, and of course press Ctrl+h, and navigate to /.local/share/Trash

and delete /files there.

Again, good luck. :-)

I'll be curious as to whether or not it will work.

---

### Post by HandleWithCare on 2009-05-06
It's a local hard drive, not a pen/stick

When I browse the folder with gksu nautilus I get the same result. The folder files is still gone since I just deleted it.

When I click on the trash icon I get the following error:
```

The folder contents could not be displayed.

Sorry, could not display all the contents of "trash": Operation not supported

```

---

### Post by BslBryan on 2009-05-06
Well, first, if there's *anything* in the /Trash folder, delete it.  If that doesn't work, then it's most likely a problem with root's trash.  So, in the terminal
```
gksudo nautilus
```

then in the address bar:
```

/root/.local/share/Trash

```

Also, if you're on Ibex, I remember a workaround for not being able to remove trash, if neither of these work.

Good luck. :-)

---

### Post by HandleWithCare on 2009-05-06
I think I found what's went wrong. All of the files in the trash folder came from another partition (than the one my home is on). In the root of this partition was a .Trash folder with folders files and info. I deleted this .Trash folder and now the files are finaly gone. 
Although this particular case is solved I think this i s a serious problem in ubuntu. What do you think, is this a bug?

---

### Post by BslBryan on 2009-05-06
Well, I mean, there are definitely reasons why it may seem like a bug.

I think, however, that it does what it was meant to do.  It deletes the files from a certain directory.

Things go wrong here when the trash is located somewhere other than what is specified in the code. 

I suppose a good workaround for you is to rewrite the code, and make it delete the trash from /.local/share/Trash, as well as /root/.local/share/Trash, and the path where you found your trash in the separate partition.  This way, it will all be covered whenever you hit "empty trash."

---

### Post by HandleWithCare on 2009-05-06
I'm not sure I agree with 'it does what it's supposed to do', because when I see files in the trash I expect them to be deleted when I hit empty trash.  By the way, if it can display the files as being trash, why can't they be deleted. In my opinion it should not be necessary to edit code in an os t make it work as you'd expect.
Anyway, it works...

---

### Post by sdowney717 on 2009-05-06
I had this type of problem once before. YES! I agree completely, if it is trash then it should trashable.
Perhaps It ought to at least tell you why it cant delete the trash files. In a way that people can understand.

---

### Post by BslBryan on 2009-05-06
Well, I mean, trash is sent to a certain path.  When you empty trash, the trash program deletes all files in the folder it's been directed to by the program.  

If there are no files in that folder, the trash is just as confused as you are.

You are right in the sense that, no, it makes absolutely no sense that emptying the trash doesn't empty the trash.  It's like a piece of gum being stuck to your trash can, and no matter how hard you try to empty it, it just stays in there.  

The only workaround is to reach in there are pull it out, and nobody wants to do that.

So, yes, I believe it can be improved upon, greatly.  But my opinion still stands that it is not a bug, necessarily. 
:P

---

### Post by silbar on 2009-05-07
Thank you, HandleWithCare, for discovering what was wrong and reporting how you fixed it.  I had exactly the same problem with a folder that appeared in the trash after a re-install of Hardy 8.0.4.  In my case the culprit folder was /.Trash-1000/, which was apparently owned by me, not root.  (I rm'd it as root, anyway, since I was there at the time.)

Dick Silbar

---

### Post by HandleWithCare on 2009-05-07
well, lets mark it as solved then. Thanks everybody for your input!

edit:
eehm, how do I mark it as solved, can't find the option...

---

### Post by baba88 on 2011-01-25
I have this same problem but I could not understand how to solve it.
Could you clarify please?

---

### Post by fugowie42 on 2012-12-26
Just wanted to thank the poster here, and confirm the fix! 

I, too, had a phantom file in the .Trash of my home partition which was somehow a trace of the trash left in a flash drive, and deleting the file from the flash drive also removed it from my home trash. 

The only (small, and possibly obvious) thing I would add, is that I had to first hit 'ctrl+h' in my empty flash drive from nautilus to reveal the trash folder and its lurking contents. 

Thanks again!

---

