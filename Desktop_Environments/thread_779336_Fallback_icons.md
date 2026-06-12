---
title: "Fallback icons"
date: 2008-05-02
forum: Desktop Environments
---

### Post by Sugz on 2008-05-02
Hello!
I was wondering today whiles changing my desktop theme if there was any way to change the fallback icons that Ubuntu uses when icons in a new theme are not found. 
You should know what i mean when you install a new icon theme with some icons missing, ubuntu replaces them with horrible default ones. 
Is it possible to the change the icons that ubuntu uses?

Thanks

-Sugz

---

### Post by Sugz on 2008-05-02
Just found the answer so ill post his answer for anyone that is interested. 

ON behalf of Garba

"forgive me if this tip might sound paultry, but I didn't know about this and now that I do, my life is taking a turn for the better. Very often that nice icon theme you've just dl'ed is missing some icons. Likewise, there might be a similar looking theme which provides icons which might be a good replacement (actually, a "filler"). Hence, do as follows: go to the theme folder and open the index.theme file and look for the "inherits" entry: add, in order of preference, the icon theme gnome should use as a fall back when some icon is missing, and you are all set (actually you have to use the folder name the icon theme you're using as fallback is stored in, and to my knowledge it gotta be either in the /usr/share/icons or ~/.icons location). I hope this little tip might come in handy for all the friends here who didn't know about this nifty trick. Regards, andre"

PLease note: this is not my suggestion, all credit should go to Garba

Thanks

---

