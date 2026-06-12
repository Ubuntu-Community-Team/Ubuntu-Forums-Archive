---
title: "Can I change the encoding option in OpenOffice 2.0 Calc?"
date: 2007-03-02
forum: Desktop Environments
---

### Post by snowboard975 on 2007-03-02
I have a problem in reading an excel file in Korean.
But I guess it is because the encoding is not inappropriate. (I can see Korean in other excel files except it and there are a couple of encoding types in Korean)
I tried to find any menu to change the encoding option in the OpenOffice 2.0 Calc, but couldn't find it.
Does anyone know how to change the encoding option in it??
Thanks

---

### Post by fourchannel on 2007-03-03
Try going to Tools -> Options -> Language Settings -> Language:

At the bottom is a checkbox for "enable support for aisian languages"

See if that works. If not you might have to install a korean language local or something.

If that doesn't fix it, then install full korean language support:

```
sudo apt-get install language-support-ko
```And then go back to open office language settings and where it says "Default languages for documents", add korean under the aisian document.

---

### Post by snowboard975 on 2007-03-03
Thank you for your consideration. Language-support-ko package is already installed and the "Default languages for documents" in the openoffice language settings is already set to Korean. Still, I can't see Korean in the excel file. Well, I guess this is because that the excel file has different encoding other than ko_KR.UTF-8
Is there any other way that I can see the excel file?

---

