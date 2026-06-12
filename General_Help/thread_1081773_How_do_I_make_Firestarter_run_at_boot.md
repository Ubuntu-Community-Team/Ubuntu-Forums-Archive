---
title: "How do I make Firestarter run at boot?"
date: 2009-02-26
forum: General Help
---

### Post by s3a on 2009-02-26
Whenever I boot my computer and log into my account, Firestarter is NOT in the top panel (indicating that it is running). I would like it to be there automatically at boot. How do I do that?

Any help would be greatly appreciated!
Thanks!

---

### Post by dox_drum on 2009-02-26
Perhaps it's a silly question, but Did you put it in the list of startup programs?

---

### Post by mb_webguy on 2009-02-26
Firestarter is just a configuration GUI for iptables, which is always running.  You don't have to have Firestarter running for your firewall to be doing its job.

---

### Post by abn91c on 2009-02-26
add it in you sessions manager
the command is gksu /usr/sbin/firestarter

---

### Post by UbuntuNerd on 2009-02-26
you can always type this command in a terminal to check your firewall status:
```
sudo /etc/firestarter/firestarter.sh status
```

---

### Post by matsberglund on 2009-03-20
Thanks a lot for the explanation. I thought Firestarter wasn't running because I saw no icon.. 

Now I know better (there *are* actually things happening inside my computer which I cannot see... hmm).

---

