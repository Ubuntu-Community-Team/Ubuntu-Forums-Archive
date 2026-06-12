---
title: "firefox security upgrade breaks dom inspector"
date: 2006-06-12
forum: Desktop Environments
---

### Post by s_p_a_r_k_y on 2006-06-12
Hi, apt greets me with this messages after I wanted to re-install the dom-inspector for firefox. 
```

The following packages have unmet dependencies:
  firefox-dom-inspector: Depends: firefox (= 1.5.dfsg+1.5.0.3-0ubuntu3) but 1.5.dfsg+1.5.0.4-0ubuntu6.06 is to be installed
E: Broken packages
```

Is there another way to get the dom inspector on to my system. I rely on that friendly guy for development.

---

### Post by s_p_a_r_k_y on 2006-06-14
Nothing? No one has any idea how to install the dom-inspecor? Can I move the mozilla-dom-inspector over to firefox? I need some kind of dom-inspector

---

### Post by dabang on 2006-06-14
Same problem with thunderbird and enigmail. I guess we have to wait for updates for enigmail and dominspector...

---

### Post by s_p_a_r_k_y on 2006-06-15
I have installed mozilla (the big beast) for its dom inspector. I guess its not bad having 2 browsers around anyway for webdevelopment so you can test things while being logged in to a website and while being a guest or so. Still would like the dom inspector for firefox tho

---

### Post by kimu on 2006-07-27
I had the same problem. I fixed this problem just copying the dom inspector folder from an existing ubuntu installation with firefox and inspector already installed and paste it in the /home/account/.mozilla/firefox/extensions folder or you can also paste it in the usr/lib/firefox/extensions to make it accessible fom all users.

You can download the dom inspector folder here (attached file)

Bye

---

### Post by opioid on 2006-10-15
WTF Ubuntu? No Dom Inspector?

THANKS kimu...

---

