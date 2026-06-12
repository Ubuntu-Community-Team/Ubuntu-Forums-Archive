---
title: "Lubuntu 14.04 right click trash icon desktop to empty?"
date: 2014-04-26
forum: Desktop Environments
---

### Post by stinger30au on 2014-04-26
by right clicking the desktop and clicking desktop preferences and then desktop icons and selecting show trash can on desktop, i now have the trash can on the desktop and thats all well and dandy & almost halfway to where i want to be.

I would like the abilty to be able to right the trash can and select something that will delete all files contained it it rather then open pcmafm and do it thru there. i have hunted high and low with google and i can not for the life of me find the answer. i have spent ages going thru menus and settings that i can find in lubuntu and i come up enpty handed as well.

any one got any ideas/suggestions/thoughts/comments etc?

thanks

---

### Post by Dennis N on 2014-04-26
> any one got any ideas/suggestions/thoughts/comments etc?

I think this is going to be possible with the new "custom actions". I haven't had a chance to look into them yet, but will soon.

Get started here:

[http://lubuntublog.blogspot.com/p/actions_24.html](http://lubuntublog.blogspot.com/p/actions_24.html)

---

### Post by stinger30au on 2014-04-27
aaaahhhh that looks promising. a quick google gives us this

[http://ubuntuforums.org/showthread.php?t=812712](http://ubuntuforums.org/showthread.php?t=812712)

how to delete trash from command line cos i suspect we will need to make a command that runs from shell, so we will need this

rm -rf ~/.local/share/Trash/files/*

i will keep reading and see if there is anything else we might need. with a bit of luck it might be pretty simple to do

---

### Post by stinger30au on 2014-04-27
ok, im on the right track. i followed this

[http://madebits.com/blog/comments.php?y=14&m=03&entry=entry140317-141947](http://madebits.com/blog/comments.php?y=14&m=03&entry=entry140317-141947)

and i had to create a new directory

[I]~/.local/share/file-manager/actions/

[/I]in there i created a new text file and now i can right click on the desktop any where and i can see

empty trash

but if i click on the empty trash it does nothing. here is what is in my "empty.trash.can.desktop" file


[Desktop Entry]
Type=Action
Tooltip=Empty Trash Can
Name=Empty Trash Can
Profiles=profile-zero;

[X-Action-Profile profile-zero]
MimeTypes=inode/directory;
Exec=rm -rf ~/.local/share/Trash/files/*
Name=Default profile


im close, very close, i need to do some more reading but i think this is going to work, if i can read and understand how it works moreclearly

---

### Post by stinger30au on 2014-04-27
i just tested this 

rm -rf ~/.local/share/Trash/files/*

stright from shell and it works perfectly. so there is something that i need to fix in the little bit of code....mmm.. but what on earth is it, lol

---

### Post by stinger30au on 2014-04-27
i went reading and i thought if i remvoed this from the text file

MimeTypes=inode/directory;

that it would work, but i have logged off/on and it dint work. *sigh* man i thought it was going to be the missing bit hat fix it. oh man, this is so frustrating, im so close to getting this working i can smell victory, but man, what is stopping it from not working??? AAARRRGGGHHH!!!

lol

---

### Post by vasa1 on 2014-04-27
> **stinger30au said:**
> i just tested this 

rm -rf ~/.local/share/Trash/files/*

stright from shell and it works perfectly. so there is something that i need to fix in the little bit of code....mmm.. but what on earth is it, lol
Just a wild guess but your command is meant to work from a terminal and so maybe PCManFM doesn't know how to deal with it in a Custom Action?

This is an interesting thread and I hope you get what you want!

---

### Post by sudodus on 2014-04-27
Maybe ~ or * is not expanded correctly from the desktop file (as bash would expand them). Start with your hardcoded home directory instead of ~

---

### Post by stinger30au on 2014-04-27
lol, you must have mistaken me for someone who actually has an idea on what they are doing here, lol. im doing lots of reading and experimenting here trying to get this to work & i have got *zero* idea what your talking about, sorry.

---

### Post by stinger30au on 2014-04-27
after more reading here, it looks like i might need to create a new text file and call that when the "empty trash" is selected. looks like pcman fm wont run sheel command directly, hence the need for the extra text file. i think if i make it so when you select "empty trash" it runs the extra text file it iwll run it direct form sheel and bypass pcman and it will work.


thats the theory.... now to make it happen, lol, more reading

---

### Post by stinger30au on 2014-04-27
readin thru here

[http://madebits.com/blog/comments.php?y=14&m=03&entry=entry140317-141947](http://madebits.com/blog/comments.php?y=14&m=03&entry=entry140317-141947)

this is where i got the idea of the extra text file and in there put the shell command to delete all trash from shell. this might be the key im looking for to make it work

---

### Post by stinger30au on 2014-04-27
i wonder if i modify this

#!/bin/bash

folder=$(zenity --file-selection --directory --title="Copy To Folder")
if [[ $folder ]]; then
	# cp -r $@ "$folder"
	for var in "$@"
	do
	    cp -r "$var" "$folder"
	done
fi


and make it real simple and make it say this


#!/bin/bash

rm -rf ~/.local/share/Trash/files/*



i wonder if that is the secret....mmmmm... damn it and i got to go out for a while. *sigh* hopefully someone else might find this interesting and keep working on it while im gone, lol

---

### Post by sudodus on 2014-04-27
> **sudodus said:**
> Maybe ~ or * is not expanded correctly from the desktop file (as bash would expand them). Start with your hardcoded home directory instead of ~

> **stinger30au said:**
> lol, you must have mistaken me for someone who actually has an idea on what they are doing here, lol. im doing lots of reading and experimenting here trying to get this to work & i have got *zero* idea what your talking about, sorry.

Let us say that your user id in the computer is stinger, then your hardcoded home directory is
```

/home/stinger
```

so use that instead of ~ and

```
~/.local/share/Trash/files/*
```

becomes

```
/home/stinger/.local/share/Trash/files/*
```

---

### Post by stinger30au on 2014-04-27
> **sudodus said:**
> Maybe ~ or * is not expanded correctly from the desktop file (as bash would expand them). Start with your hardcoded home directory instead of ~

i have done some more reading & reread what you typed and now i under stand what you mean . i will try this now

---

### Post by stinger30au on 2014-04-27
ah ha!!!!!


it now works!

i made the full data path as the moderator said and tried it and it works beautifully!

you must put in the *FULL* file path to the trash and it works like a charm!!!


Woo-hoo!!!

Im over the moon. i have done much googling on this topic and people have been asking for this function for a number of years now, lol!!


Yippie!

Team work at its best, this is awesome!

Thanks so much all, i really appreciate your help

---

### Post by sudodus on 2014-04-27
Congratulations :KS

---

### Post by stinger30au on 2014-04-27
> **sudodus said:**
> Congratulations :KS

Thank you for your assistance & thanks to "Dennis N" who suggested where to start looking in the first place :D

---

