---
title: "Where does Java 1.5.0  install? Azureus reports older version installed.."
date: 2006-07-17
forum: Desktop Environments
---

### Post by tonym2 on 2006-07-17
I tried installing Azureus and Java 1.5.0. Although both report to be installed ok (no errors after installaton) Azureus won't work at all. IF I get it to launch, the only thing I can get to come up is the about page which reports that version 1.4.2 is the Java version that is installed/being used by Azureus.

Now I KNOW I installed 1.5.0. I see links to it in Applications -> Internet and System -> Preferences.Reload this Page  Anyone seen this before?
	
Why does Azureus think that version 1.4.2 is installed?

Secondly, where does Java version 1.5.0 install itself? I've looked in /usr/local and /user/bin and  all the usual places. I can't see where it's installed.

Can anyone help me?

---

### Post by littlespy on 2006-07-17
You have multiple versions of java installed.  You can choose the default one by opening a terminal and typing

> sudo update-alternatives --config java

---

### Post by tonym2 on 2006-07-17
Littlespy, you are a genius! that worked! Thanks so much!

Tony

---

