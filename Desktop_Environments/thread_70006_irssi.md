---
title: "irssi"
date: 2005-09-28
forum: Desktop Environments
---

### Post by vladuz976 on 2005-09-28
i am trying to figure out how to make irssi auto join channels after starting it.
i've read and followed instructions and even used their examples. autoconnecting to freenode for example works fine, but it just doesn't join channels. 
if anybody knows how to please let me know.

---

### Post by tomchuk on 2005-09-28
in ~/.irssi/config you can do something like the following:
```

chatnets = {
[INDENT]freenode = {
type = "IRC";
autosendcmd = "/^msg NickServ identify <password>";
max_kicks = "4";
max_modes = "4";
max_msgs = "1";
max_whois = "1";
};[/INDENT]
}
channels = ([indent]
{ name = "#debian"; chatnet = "freenode"; autojoin = "No"; },
{ name = "#ubuntu"; chatnet = "freenode"; autojoin = "Yes"; }
[/indent]
);

```
note the autojoin option for the channels.

---

