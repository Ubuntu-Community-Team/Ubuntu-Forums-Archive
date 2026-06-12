---
title: "Chinese fonts weird"
date: 2005-07-28
forum: Desktop Environments
---

### Post by wokick on 2005-07-28
Just installed Ubuntu Hoary on my IBM T41 laptop. I was impressed--every piece of hardware just works right out of the box, which saved me lots of time to tweak things. However, I can't get the Chinese display perfect. 

The attached screenshot shows chinese characters in firefox browser. As you can see, these characters are not in the same size. This problem happens when I input chinese in gedit or other input dialogs, and in the window title. 

After runned "dpkg-reconfigure -i locales" to configure all the zh_CN related locales, and set LC_CTYPE to zh_CN.gb2312, only the window title went back to normal. 

I googled this whole morning, but couldn't find any way to solve this last problem. 

FYI, the LANG argument is set to "en_US.UTF-8". 

Thanks for any suggestions!

---

