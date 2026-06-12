---
title: "Delete spaced directory"
date: 2005-12-29
forum: Desktop Environments
---

### Post by AllanP on 2005-12-29
I copied My Documents from Widows to Ubuntu. Now I want to delete "My Music". I go to change the attributes and Linux doesn't recognize the two name format. Response is:
" chmod: cannot access `My': No such file or directory
chmod: cannot access `Music': No such file or directory "

---

### Post by thekiller on 2005-12-29
if you just wanna delete it then do 

rm -rf  My\ Music/

---

### Post by AllanP on 2005-12-29
Thanks; now I get this:

" chmod 777 My\ Music/
chmod: changing permissions of `My Music/': Operation not permitted "

---

### Post by Zalbor on 2005-12-29
General info: A space is a special character (separates commands from their switches etc). In order to cancel a special character, as you try to do with space, you put \ before it.

About this: Is the directory in a FAT partition maybe? If it isn;t, then maybe you don't have permission to change the attributes (though you should if it was you who copied it). Try the same commad with 'sudo' in the beginning. This will give you root access and take it back when the action has finished.

---

### Post by thekiller on 2005-12-29
to use chmod you have to be superuser 

sudo chmod 777 My\ Music/

---

### Post by trash on 2005-12-29
the trick with name spaced directories is that linux sees the space as a separation, like two seperate commands. In order for linux to view it as one command/item you need to enclose with quotes..

ex.
cd "/home/user/My music"

---

### Post by AllanP on 2005-12-29
Oh Jeez how stupid of me; of course. Gotta blame it on the age thing.



Thanks again for your speedy response:D

Shoulda quoted but, response in regards to the sudo.

---

### Post by Zwack on 2005-12-29
Either quoting the whole thing...

rm -rf "/home/user/My Music"

or escaping the space

rm -rf /home/user/My\ Music

should work.

Neither one is more correct than the other.

Z.

---

### Post by AllanP on 2005-12-29
Thanks all for the help; worked great.

Regards, Allan:D

---

### Post by kperkins on 2005-12-29
and chmod doesn't delete anything, by the way--it just changes the permissions. If you want to delete it then just use the code given above, you don't need to change permissions to do that.
(and **thekiller** you don't need to sudo to chmod a file/directory if you own it, the only reason to sudo is if root (or someone other than the current user) owns the file/directory--which seems to be the case in this instance)

---

### Post by thekiller on 2005-12-29
i actually thought so too, and thats why didnt point it out the first time. Looking at the error "Operation not permitted" I guessed u might need to be root to do that. Anyway, thanks for the pointer ! :p

---

### Post by kperkins on 2005-12-29
Ah, the way your post was written it looked like you meant that it had to be done that way all the time.
That's one of the problems with message boards sometimes, trying to get the meaning of the written mesage.
:D

---

