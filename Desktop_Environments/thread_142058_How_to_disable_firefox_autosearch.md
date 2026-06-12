---
title: "How to disable firefox autosearch?"
date: 2006-03-09
forum: Desktop Environments
---

### Post by jenred on 2006-03-09
Hello!

I'm in the process of attempting to completely eliminate any reliance on my WindowsXP partition.   One of the very last annoyances with Ubuntu is the inablity to turn off the autosearch function in the firefox address bar.  For example:

I am connected to a remote LAN via VPN (pptp).  I enter the short site name -- for these purposes let's say the site is called "badger" -- into the address bar:

When using firefox 1.5 in Windows XP home (connected to company via vpn) - I type "badger" in the address bar and viola! The badger site comes up (badger is only accessible internally).

Now when using Ubuntu and firefox 1.5 (thought maybe the autosearch was a 'feature' of 1.07 so I upgraded) I connect to the LAN no problem via VPN pptpclient works quite well -  [http://pptpclient.sourceforge.net/)](http://pptpclient.sourceforge.net/)), can ssh to the box running the badger site, no problem. However, when I type 'badger' into the address bar I am IMMEDIATELY wisked to some random site that has the word badger somewhere in the metadata, however, badger.company.com takes me to the internal site.  Now if there is an addressing problem -- fine -- I would prefer to see an http error so I can fix, but no I keep getting wisked over to some random site. 

The site "badger" is running on a RHEL box w/apache so there is no IIS strangeness going on.

I've tried changing a few variables in about:config and have been unable to get anything to disable the autosearch "feature."  Have also searched the mozilla site -- but can find no specific suggestions.

Suggestions to fix greatly appreciated!

---

### Post by 5-HT on 2006-03-09
Hey, I'm not sure why this problem came up in the switch to FireFox on Ubuntu, but by default on Linux (not sure about the widows version), keywords entered in the address bar that are not linked to any bookmarks are sent to Google's "I'm feeling lucky" search.

The about:config entry specifying which site to use for keyword search to should be:

```
 keyword.URL 
```

To turn off keyword searching from the address bar just set ```
 keyword.enabled 
``` to "false".

Apart from turning off the feature, or changing the search site...what about creating a bookmark to badger.company.com with the keyword "badger"?

(Just make a bookmark to badger.company.com, open up the bookmark manager, right click on that bookmark, and add "badger" into the keyword feild).

That way, "badger" should be linked to badger.company.com, and FireFox shouldn't even pass it to a search, it'll just connect to badger.company.com.

About a good knowledgebase for Mozilla products, [http://kb.mozillazine.org/Main_Page](http://kb.mozillazine.org/Main_Page) is wonderful and documents the about:config options in detail.

Hope some of this may be of some help.

---

### Post by jenred on 2006-03-09
Very helpful thank you. Keyword search is now disabled. 

However now when I enter [http://badger](http://badger) the browser interprets this as:

[http://www.badger.com](http://www.badger.com)

I am logging into the domain no problem via pptp.  

The default Windows does have the keyword search enabled -- it appears that the browser just searches a little longer for the entered address.  ?

Maybe this is a vpn/pptp issue rather then a browser issue. ? 

Thanks for your help and the pointer to the mozilla site.  I may wind up making an alias as you suggested -- however, I would like to figure out why just entering in "badger" works in the Windows firefox distro but not in Ubuntu/linux firefox distro.

The site is configured using the short-name.

There may also be some server-side config issues -- but I would really like to just get an http error if [http://badger](http://badger) isn't resolving correctly for trouble-shooting purposes.

Any other ideas re: why this is happening greatly appreciated. 

 Thanks!
  Jen

---

### Post by lamego on 2006-03-09
I have a default firefox configuration, if I specify a resolvable host it will browse the host, it will not do the google find as for any another unknown keyword.
So I would say your problem is with your DNS configuration, hosts will be lookup based on the "search" domain from your /etc/resolv.conf (usually retrieved from DCHP).

---

### Post by jenred on 2006-03-09
And that was it!  

Added a DNS search domain  for the active interface after connecting.  PPTP connection was adding IP's for DNS servers -- but needs the server domain for resolution of the shortnames.

Now to figure out how to modify pptpclient to add the search domain to the temporary resolv.conf!  

Thanks!

---

