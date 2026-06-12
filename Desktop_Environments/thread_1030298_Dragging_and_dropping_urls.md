---
title: "Dragging and dropping urls"
date: 2009-01-04
forum: Desktop Environments
---

### Post by GrahamM on 2009-01-04
I tried asking this in the General forum, but no responses. Maybe this would be a better place?

[http://ubuntuforums.org/showpost.php?p=6483850&postcount=1](http://ubuntuforums.org/showpost.php?p=6483850&postcount=1)

Basically asking why dragging and dropping a url from Firefox address bar to Desktop results in different results for different sites.

---

### Post by hansdown on 2009-01-04
Hi GrahamM.
This might be helpful.

[http://cybernetnews.com/2008/04/05/helpful-tip-drag-drop-texturls-in-firefox/](http://cybernetnews.com/2008/04/05/helpful-tip-drag-drop-texturls-in-firefox/)

You can copy and paste your orinal question into the searchbar to get more info.

---

### Post by GrahamM on 2009-01-04
> **hansdown said:**
> Hi GrahamM.
This might be helpful.

[http://cybernetnews.com/2008/04/05/helpful-tip-drag-drop-texturls-in-firefox/](http://cybernetnews.com/2008/04/05/helpful-tip-drag-drop-texturls-in-firefox/)

You can copy and paste your orinal question into the searchbar to get more info.

I have posted question in Mozilla Firefox forum as well. But, thanks for link anyway!

---

### Post by bunty on 2009-01-06
you're probably looking at this the wrong way around. It's not a question of which site you pull the URL from but the type of file that you are pulling the URL of.

You don't say exactly what you are dragging so it's hard to guess.

What happens when you click on the desktop icon depends on your desktop manager. If you drop an URl  it will likely trigger a different response to an image. If the url has what MS calls a file extension it will probably be presumed to indicate what the url refers to (although this could be completely wrong and misleading). The server will usually provide content-type information to the browser.

If it does not then the browser (user-agent) can examine the byte stream to try to determine the data type. eg the first four bytes is often a file type signature. To that extent it could depend on the server, ie the site.

HTH

---

### Post by GrahamM on 2009-01-07
> **bunty said:**
> you're probably looking at this the wrong way around. It's not a question of which site you pull the URL from but the type of file that you are pulling the URL of.

You don't say exactly what you are dragging so it's hard to guess.

You must not have read the first post - it linked to my post in General where I gave this information. (I have reposted it below.)

>  What happens when you click on the desktop icon depends on your desktop manager. If you drop an URl  it will likely trigger a different response to an image. If the url has what MS calls a file extension it will probably be presumed to indicate what the url refers to (although this could be completely wrong and misleading). The server will usually provide content-type information to the browser.

If it does not then the browser (user-agent) can examine the byte stream to try to determine the data type. eg the first four bytes is often a file type signature. To that extent it could depend on the server, ie the site.

HTH

You are probably right here that somehow the url is providing different information to the Desktop (Nautilus). But, this does not happen when the same url is dragged to the Desktop from the Firefox address bar in Windows, so this is presumably a Ubuntu problem? Another one of those quirky things?

Original Post in General:

[http://ubuntuforums.org/showpost.php?p=6483850&postcount=1](http://ubuntuforums.org/showpost.php?p=6483850&postcount=1)

this is what it said:

```
 Dragging urls to DEsktop - Different results?
When I drag a url from the Firefox address bar to the Desktop. I get different results for different sites.

In one case, I get the Globe Icon indicating a conventional link. When I click on the link, it opens the website as it should.

In the other case, dragging results in a smaller globe set on a sheet of paper as the icon. When I click on this, it gives option as to which program to use to open it - presumably a browser or a text/html editor (see Kijiji properties.png below)

In both cases, I can open the website. But in second one I must chose Firefox. Once open, the second type shows a link to a file in the address bar instead of the web address. (See Screenshot.png attached)

I don't know if this will happen for others. The url in my example is :
http://kingston.kijiji.ca/f-buy-and-sell-W0QQCatIdZ10

Anyone know why I get this different behaviour with different websites?
Attached Thumbnails

```

---

### Post by mcduck on 2009-01-07
I've found that the best way to drag&drop desktop links from Firefox is to not drag the address bar, but instead drag from tabs..

---

### Post by GrahamM on 2009-01-07
> **mcduck said:**
> I've found that the best way to drag&drop desktop links from Firefox is to not drag the address bar, but instead drag from tabs..

Tried that, but result is same for the url in question ( [http://kingston.kijiji.ca/f-buy-and-sell-W0QQCatIdZ10](http://kingston.kijiji.ca/f-buy-and-sell-W0QQCatIdZ10)
 )  It drags and drops OK, but icon is different and Firefox does not start automatically - needs an extra step.

If I delete /f-buy-and-sell-W0QQCatIdZ10 and enter [http://kingston.kijiji.ca](http://kingston.kijiji.ca) Firefox adds a "/" and displays [http://kingston.kijiji.ca/](http://kingston.kijiji.ca/) which then opens.

If I drag this to the Desktop, I get an error message (see below) regardless of whether I drag the address bar or the tab.

So, this seems to be a second problem with drag and drop in Ubuntu. Windows handles these actions without a problem. 

These are not huge problems, but along with other quirks, the kind of thing that would prevent me from installing Ubuntu on the other computers I look after (wife, neighbours, friends). But I am having fun exploring Ubuntu :)

Graham

---

