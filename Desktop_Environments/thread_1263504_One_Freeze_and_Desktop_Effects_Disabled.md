---
title: "One Freeze and Desktop Effects Disabled"
date: 2009-09-11
forum: Desktop Environments
---

### Post by Callaine on 2009-09-11
The only problem I have with Ubuntu is that about once a month, when I have desktop effects enabled my system freezes. After about thirty seconds all returns to normal, except that Desktop Effects are disabled.

I have a nVidia 6600 graphics card which I know is known to have problems with Desktop Effects. 

But I can run it for a very long time before a problem occurs at the extra setting.

I can re-enable desktop effects by removing the nVidia driver, rebooting, re-enable the nVidia driver, rebooting again and then I can enable Desktop Effects Extra and I am good for another month or two, until I am viewing some obsure webpage and my system freezes and it back to the same cycle.

I think a much better way to handle this situation is that when a system instability occurs, instead of just disabling Desktop effects, a dialog would appear that Desktop Effects might cause instability on your system, do you want to keep it in spite of this or disable it. the decision should be up to the user. I don't like my OS making that decision for me.

---

### Post by earthpigg on 2009-09-11
hi,

there is a good chance you do **_not_** need to restart your entire computer.

press ctrl+alt+f4 (or f5 or f6, etc)

login using your normal username/password.

type this when you can:

```
sudo killall _X_org
```

press ctrl+alt+f7 to get back and see your login screen.

you can test this right now with_*out*_ killing X or any other madness. do ctrl+alt+f4 or f5 or f6. **ctrl+alt+f7 will immediately bring you back home**.

compiz (also known as "*desktop effects*") is buggy. few will deny that. but those fancy cubes and wobbly windows sure do look cool, don't they??! :D

to quickly disable it: alt+f2 and then "metacity --replace"
to quickly bring it back: alt+f2 and then "compiz --replace"

---

### Post by 3rdalbum on 2009-09-11
> **Callaine said:**
> I think a much better way to handle this situation is that when a system instability occurs, instead of just disabling Desktop effects, a dialog would appear that Desktop Effects might cause instability on your system, do you want to keep it in spite of this or disable it. the decision should be up to the user. I don't like my OS making that decision for me.

But here's the thing: How does Ubuntu detect the instability and determine that it is caused by the graphics driver? Should we be putting in all sorts of developer time to work around problems in a binary blob, rather than working on Free Software? And have you tried merely upgrading your driver to the latest version; it really can fix instabilities.

---

