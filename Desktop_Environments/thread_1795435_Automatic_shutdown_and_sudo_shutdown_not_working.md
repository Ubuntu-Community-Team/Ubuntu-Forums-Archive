---
title: "Automatic shutdown and sudo shutdown not working"
date: 2011-07-02
forum: Desktop Environments
---

### Post by Dáire Fagan on 2011-07-02
Automatic shutdown and sudo shutdown are not working as they should.

Automatic shutdown seems to work some of the time, and other times it does not. Is it affected by VLC playing videos?

Sudo shutdown used to work perfectly, but now the system goes on past the specified shutdown time apparently oblivious.

The command I am using is:

```
sudo shutdown -g hh:mm
```

Any ideas?

Thanks.

---

### Post by Toz on 2011-07-02
I saw the command you entered and thought, "-g isn't a valid parameter". I did a **man shutdown**, and sure enough, there is no g parameter listed. On a hunch, I ran the same command and got sort of a shutdown. Not a complete shutdown, but apparently -g _is_ a valid parameter.

I would suggest trying:
```
sudo shutdown -h <hh:mm>
```And hh:mm needs to be in 24-hour format.

---

### Post by Dáire Fagan on 2011-07-05
> **Toz said:**
> I saw the command you entered and thought, "-g isn't a valid parameter". I did a **man shutdown**, and sure enough, there is no g parameter listed. On a hunch, I ran the same command and got sort of a shutdown. Not a complete shutdown, but apparently -g _is_ a valid parameter.

I would suggest trying:
```
sudo shutdown -h <hh:mm>
```And hh:mm needs to be in 24-hour format.

That's seems to do it, thanks. 

I was using the 24 hour format before, so it must have been the -g argument that was stalling it.

---

