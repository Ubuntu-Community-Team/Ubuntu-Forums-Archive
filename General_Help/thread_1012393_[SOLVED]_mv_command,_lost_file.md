---
title: "[SOLVED] mv command, lost file"
date: 2008-12-15
forum: General Help
---

### Post by notsomeone on 2008-12-15
I did: `mv ./repeat.vim ..//vim` when I meant `mv ./repeat.vim ../.vim`
That first destination doesn't exist, but my file disappeared and didn't reappear anywhere. Is it gone forever?
I tried updatedb & locate repeat.vim but it's not listed.
Just curious. I can redownload the file

---

### Post by blazemore on 2008-12-15
> **notsomeone said:**
> I did: `mv ./repeat.vim ..//vim` when I meant `mv ./repeat.vim ../.vim`
That first destination doesn't exist, but my file disappeared and didn't reappear anywhere. Is it gone forever?
I tried updatedb & locate repeat.vim but it's not listed.
Just curious. I can redownload the file

Can you do
```
mv ..//vim ../vim
```

---

### Post by notsomeone on 2008-12-15
Ohhh, I see what happened.

This is the output that command gives me.
mv: `..//vim' and `../vim' are the same file

So I noticed that the file was renamed to 'vim' instead of moving the file to the .vim folder. Thanks.

---

