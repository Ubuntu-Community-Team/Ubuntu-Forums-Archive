---
title: "How can I search files in lxde ?"
date: 2012-05-28
forum: Desktop Environments
---

### Post by DaviesX on 2012-05-28
I have installed lxde on unbuntu for some time. But the default file manager, pcmanfm, seems doesn't have file searching function. Can you tell me how to search files on pcmanfm, or how can I change to some other useful file manager ? 

Thanks :)

---

### Post by Rex Bouwense on 2012-05-28
I believe Ctrl F is what you are looking for.

---

### Post by DaviesX on 2012-05-29
No, it doesn't work. It can only search for the file on the current level of directory, and it can't match the file name correctly either =,=

---

### Post by Dennis N on 2012-05-29
I would instead use the find command. Navigate to top level directory needed, then

find ./ -iname "<search string here>"

Find filenames containing the string 'dog'

find ./ -iname "*dog*"

It searches subdirectories in the process. -iname makes it not case sensitive.

---

### Post by PhilGil on 2012-05-29
If you prefer a GUI tool, catfish is a popular front end for the search and find commands. It's available in the Universe repo.

---

### Post by Theredbaron1834 on 2012-05-29
There is now an lxde finder, called LXFind. It wasn't ready to get added to lubuntu before the feature freeze, but you can find it at the lubuntu ppa [here]("https://launchpad.net/%7Elubuntu-desktop/+archive/ppa"). It is simple, light, and fast. Much like Lxde itself. I like it.

You can also get lxscreenshot too. :)

---

### Post by cortman on 2012-05-29
PCManFm is probably the lamest file manager in existence, IMHO. It has virtually no search function, as you found out.
What I did was remove it and install Thunar- just as lightweight and has full search functionality, plus a few other options.
Or if you prefer to keep PCManFm, install catfish to search with.

---

### Post by DaviesX on 2012-05-29
Thanks you guys :)

For your post, can you please tell me how to change pcmanfm to Thunar since I don't know how to operate, Thank you.
> **cortman said:**
> PCManFm is probably the lamest file manager in existence, IMHO. It has virtually no search function, as you found out.
What I did was remove it and install Thunar- just as lightweight and has full search functionality, plus a few other options.
Or if you prefer to keep PCManFm, install catfish to search with.

I think adding a search function would be that hard(just recursively loop all the directories and match the pattern, I guess), they should have proposed this function while they were designing it. I think I will install other file manager and try that later if possible. Thanks for your help any way :)
> **Theredbaron1834 said:**
> There is now an lxde finder, called LXFind. It wasn't ready to get added to lubuntu before the feature freeze, but you can find it at the lubuntu ppa [here]("https://launchpad.net/%7Elubuntu-desktop/+archive/ppa"). It is simple, light, and fast. Much like Lxde itself. I like it.

You can also get lxscreenshot too. :)

---

### Post by DaviesX on 2012-05-29
> PCManFm is probably the lamest file manager in existence
I just looked up the information about that author, and now I wonder. He is a doctor in Taiwai, he might did this in part-time. Probably he didn't have time taking care of this project... But thanks for his effort making this anyway:)

---

### Post by cortman on 2012-05-29
Right; I shouldn't be so harsh, I guess. It's definitely a better file manager than I could write, I'm guessing, but it still leaves me very unsatisfied.
You can install Thunar by running

```
sudo apt-get install thunar
```

and uninstall PCManFm by running

```
sudo apt-get remove pcmanfm
```

---

### Post by Theredbaron1834 on 2012-05-29
> **cortman said:**
> PCManFm is probably the lamest file manager in existence, IMHO. It has virtually no search function, as you found out.
What I did was remove it and install Thunar- just as lightweight and has full search functionality, plus a few other options.
Or if you prefer to keep PCManFm, install catfish to search with.
 
I mostly agree, though I think ROX-filer is worse. I normally just install Nautilus, but I have been trying to stay with a "pure" lxde this time. So I am sticking with it for a bit. Getting sick of it though. The only file browser I like is nautilus/caja.

---

### Post by DaviesX on 2012-05-29
> **cortman said:**
> Right; I shouldn't be so harsh, I guess. It's definitely a better file manager than I could write, I'm guessing, but it still leaves me very unsatisfied.
You can install Thunar by running

```
sudo apt-get install thunar
```

and uninstall PCManFm by running

```
sudo apt-get remove pcmanfm
```

Thank you for your post. But how can I search file then, I can't find that button...:mad:

---

### Post by cortman on 2012-05-29
> **DaviesX said:**
> Thank you for your post. But how can I search file then, I can't find that button...:mad:

Ctrl+f is the fastest way to bring up the search box.

---

### Post by DaviesX on 2012-05-29
Oh, I can't. Do you mean that little box on the bottom right corner ?

---

### Post by cortman on 2012-05-30
> **DaviesX said:**
> Oh, I can't. Do you mean that little box on the bottom right corner ?

Yes. Typing Ctrl+f places your cursor in that box, so you can type "Ctrl+f" then without stopping type "documents" then press enter, and it'll search for anything called "documents"

---

### Post by DaviesX on 2012-05-30
Oh, that is not what I want, pcmanfm can do this so. Because it can't transverse the directories, plus it can't match the pattern correctly. For example, I want to search the file named "Silent Hill" by typing pattern "Hill". However, I can't find that file :mad: 
I think I have to CatFish instead. Anyway, thanks for you help :)

---

