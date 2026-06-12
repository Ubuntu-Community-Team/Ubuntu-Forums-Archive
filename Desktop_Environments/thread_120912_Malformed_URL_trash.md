---
title: "Malformed URL trash:/"
date: 2006-01-23
forum: Desktop Environments
---

### Post by Sp@z on 2006-01-23
hmm sorry to post this if it has already been posted but I have to wait 3000+ seconds or more to search the forums...........LOL it is already reported.

Anyways when I try to open my trash from the icon in my panel it gives me this message........Malformed URL trash:/  from KIOexec...... I can delete the trash but not open the trash location to view the files in there........Thanx in advance.

---

### Post by EtniesBMX on 2007-03-18
Navigate to your home folder and type the following command:
**rm -rf .dcop* .local* **

---

### Post by tictacman on 2007-04-06
> **EtniesBMX said:**
> Navigate to your home folder and type the following command:
**rm -rf .dcop* .local* **


Correct me if i'm wrong but I believe trash resides in .local and if so rm -rf is a sure way of deleting the files that trying to be rescued.

I'm also having problems with malformed url error for trash and would really like to get to the bottom of it.

I tried making a desktop to link :

```
ln -s .Trash/ Desktop/Trash
```

but I end up with a icon which when clicked brings up the open with dialogue.

The problem seems to stem from selecting an alternative file manager in kde.  I've been trying out dolphin and thunar  and they can't seem to access the trash.  However when reverting back to konqueror the trash can becomes available.

---

### Post by phenest on 2007-04-12
I have the same 'malformed URL trash:/' error. I also use Dolphin (in Kubuntu), but Dolphin CAN open the trash to view the files. I only get the error when I try to view the files from the panel applet.

---

### Post by ubromtoo on 2007-06-08
I'm using Dapper, just installed the Kubuntu-Desktop as an alternate thingo

(Gnome desktop remains the default).

   Got this same problem with Trash ; also, anything under the System Menu

gives a similar notice:

                     Malformed URL media:/.

                     Malformed URL remote:/.

                      KDEInit could not launch '/home/richard'.

                      Malformed URL home:/.

    Any suggestions ?   :(


                     but still, ain't it all kinda fun ?            :guitar:

---

### Post by raul72 on 2007-12-04
> **Sp@z said:**
> Malformed URL trash:/
had the same problem (also with the "remote:/" "home:/" "media:/" etc)
installed konqueror and problem was solved... that is.. the problem was gone in dolphine and the panel :)

---

### Post by kabronkline on 2007-12-29
After removing KDE4 RC2 and going back to KDE 3.5 I ran into similar issues; however, as pointed out previously, reinstalling Konqueror fixed the errors.
```

sudo apt-get install konqueror

```

---

