---
title: "How to restore Firefox as a default browser besides Settings-&gt;Preferred Applications"
date: 2006-11-29
forum: Desktop Environments
---

### Post by sserdyuk on 2006-11-29
I am on Xubuntu 6.06. Firefox and Thunderbird are my preferred browser/mail client suite. 

The problem came with me installing Opera to test some HTML layouts. Once installed it set itself as a default handler of http:// addresses. In other words, if I clicked on a link in Thunderbird, Opera would open.

I tried to restore my preference by going to Settings->Preferred Applications and setting FireFox there, but setting there did not make any difference.

I have finally uninstalled Opera and now links do not open at all.

Where can I look for configs that control the association between http:// links and program to start?

Please!

---

### Post by Buffalo Soldier on 2006-11-29
how about right clicking on a html file -> properties -> open with -> set to firefox.

---

### Post by sserdyuk on 2006-11-29
Yes, I forgot to mention. Thunar is set to open Firefox for html files and this part works correctly. The problem is about http:// links

---

### Post by sserdyuk on 2006-11-29
Answering my own question: Opera installed a link into /etc/alternatives.

See [here ]("http://ubuntuforums.org/showthread.php?t=238256&highlight=%2Fetc%2Falternatives") for more info.

Hope it helps someone later.

---

### Post by jis on 2006-12-10
Additional information for Xubuntu users [here]("http://www.ubuntuforums.org/showpost.php?p=1488004&postcount=24").

---

