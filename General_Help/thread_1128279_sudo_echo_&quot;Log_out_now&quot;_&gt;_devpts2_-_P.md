---
title: "sudo echo &quot;Log out now&quot; &gt; /dev/pts/2 - Permission denied"
date: 2009-04-17
forum: General Help
---

### Post by ncmncm on 2009-04-17
Hi 

I want to first send a message and then log out another user connected through PUTTY .

I am aware of write but I want to  know the reasons why the following does not work

```
sudo echo "Log out now" > /dev/pts/2
``` 
I get  a permission denied error message.

Permissions on /dev/pts/2
```
crw--w---- 1 indigo tty 136, 2 2009-04-17 16:59 /dev/pts/2
```

My questions are:

1. Why. as admin this is not allowed with the existing permissions.
2. Can I  change the  default permissions for all remote machines that  connect so as to enable  me  do  the above?

Help much appreiated.

---

### Post by Bachstelze on 2009-04-17
> **ncmncm said:**
> 1. Why. as admin this is not allowed with the existing permissions.

Because this is *not* "as admin". ;) When you use Bash redirections with [font="monospace"]>[/font] the redirection is done with your normal user's privileges, not root's, so the only thing that is done "as admin" in your command is the prining of the message. Do this instead:

```
echo "Log out now" | sudo tee /dev/pts/2
```

---

### Post by ncmncm on 2009-04-17
Hi 
Thanks a bunch. Works now. 

But  still, one is  natuallry included to think that whatever  comes after the sudo should have root permissions. Any particular background to this?

---

### Post by Bachstelze on 2009-04-17
> **ncmncm said:**
> But  still, one is  natuallry included to think that whatever  comes after the sudo should have root permissions. Any particular background to this?

">" is not a command. ;) When you run

```
sudo echo "Log out now" > /dev/pts/2
```

you're telling the shell, "Run the command [font="monospace"]sudo echo "Log out now"[/font] and redrect the output to [font="monospace"]/dev/pts/2[/font]". That doesn't work because the fact that you ran a command with [font="monospace"]sudo[/font] changes nothing to the fact that the shell itself is running as yourself, and therefore can't write to [font="monospace"]/dev/pts/2[/font]. You have to do it the other way around, the other command says "run the command [font="monospace"]echo "Log out now"[/font] and then pass on the output to the command [font="monospace"]sudo tee /dev/pts/2[/font]". Since [font="monospace"]tee[/font], unlike ">" *is* a command, you can run it with [font="monospace"]sudo[/font] to write to root-owned files.

---

