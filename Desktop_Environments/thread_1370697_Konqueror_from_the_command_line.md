---
title: "Konqueror from the command line"
date: 2010-01-02
forum: Desktop Environments
---

### Post by akwatve on 2010-01-02
hi,

When I start konqueror from the command line using 

```
konqueror <URL> 
```

It opens URL in a new tab. In other words, there is a useless empty tab AND a URL tab. How I can have the desired effect of opening URL such that it is the only tab in the window ?

Thanks in advance

---

### Post by VMC on 2010-01-03
> **akwatve said:**
> hi,

When I start konqueror from the command line using 

```
konqueror <URL> 
```

It opens URL in a new tab. In other words, there is a useless empty tab AND a URL tab. How I can have the desired effect of opening URL such that it is the only tab in the window ?

Thanks in advance

I don't have that problem. Mine opens no tabs. I'm using Kubuntu testing and:
$ konqueror --version
Qt: 4.6.0
KDE Development Platform: 4.3.85 (KDE 4.3.85 (KDE 4.4 Beta2))
Konqueror: 4.3.85 (KDE 4.3.85 (KDE 4.4 Beta2))

---

### Post by akwatve on 2010-01-03
Hmm
May be thats becoz of the testing version.
Does anyone else who is using released versions see this ?

I can see it on both karmic as well as jaunty.

---

### Post by VMC on 2010-01-03
> **akwatve said:**
> Hmm
May be thats becoz of the testing version.
Does anyone else who is using released versions see this ?

I can see it on both karmic as well as jaunty.

I do have karmic installed. I'll try it and get back to you.

---

### Post by VMC on 2010-01-03
I just tried it on several web pages, and don't have tabs at the top. Only one page.

Using **Kubuntu Karmic 9.10**

$ **konqueror --version**
Qt: 4.5.2
KDE: 4.3.2 (KDE 4.3.2)
Konqueror: 4.3.2 (KDE 4.3.2)

---

### Post by akwatve on 2010-01-03
That's weird.
Just to clarify URL does not have to be a web page. I can see it even on folders.
e.g.
konqueror /home/myhomedir/

Thanks anywyas for giving it a try. May be this is some local settings issue.

---

### Post by garryknight on 2010-01-03
Have you checked your Tabbed Browsing options?

---

### Post by akwatve on 2010-01-03
Yes, I have tabbed browsing enabled. But when there is NO konqueror instance running already, shouldn't the URL be opened as a single tab. At least I would expect that there be only one tab which contains the URL. What I see is there is an empty tab and a tab containing URL. May be this is the expected behavior for the KDE team :-(

Thanks all for your time.

---

### Post by VMC on 2010-01-04
> **akwatve said:**
> Yes, I have tabbed browsing enabled. But when there is NO konqueror instance running already, shouldn't the URL be opened as a single tab. At least I would expect that there be only one tab which contains the URL. What I see is there is an empty tab and a tab containing URL. May be this is the expected behavior for the KDE team :-(

Thanks all for your time.
I think that's the problem, as Garry pointed out. My "open as tab...", is unchecked.

---

### Post by garryknight on 2010-01-04
I'm not so sure that *is* the problem. I've just tried it with 'konqueror [http://news.bbc.co.uk](http://news.bbc.co.uk) &' from a konsole and it opened with the BBC News page on a single tab. And my "Open as tab in existing Konqueror when URL is called externally" *is* checked. And now I think about it, there wasn't an existing konqueror when I ran that command. With konqueror open to a blank page, running the command again opens a new konqueror instance, again with the page on its own single tab.

---

