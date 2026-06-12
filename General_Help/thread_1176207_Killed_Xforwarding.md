---
title: "Killed Xforwarding"
date: 2009-06-02
forum: General Help
---

### Post by resonanttoe on 2009-06-02
Hi guys.

I think I've killed my Xforwarding.

Normally to get GUI access to my box, I was typing 

```
ssh -l -X -C -c blowfish user@hostname gnome-panel
```

but now when I try and start it, I'm getting 
cannot open display, 
Type gnome-panel --help for help.

The only thing that I could think that would effect it, is I followed this guide today, but I'm unsure of the relevance.

[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)

Cheers

---

### Post by resonanttoe on 2009-06-02
I've fixed this thankfully.

Just for anyone else. I found a Solution through [here]("http://ubuntuforums.org/showpost.php?p=1361790&postcount=7")

Bad permissions on the .Xauthority

Cheers guys :)

---

