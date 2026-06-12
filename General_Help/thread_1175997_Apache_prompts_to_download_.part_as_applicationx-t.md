---
title: "Apache prompts to download .part as application/x-trash."
date: 2009-06-01
forum: General Help
---

### Post by Lutrova on 2009-06-01
I have had to recently upgrade to Ubuntu Server 9 as my old hard drive decided to eat itself. I figure, why not go ahead and put on the latest one. Everything was fine until I tried to mess with the web server.

I have done NO configuration of this prior to or after this post.

I delete index.html and put all of my original files from the old server into /var/www. Instead of serving any web pages, it tries to serve and download a garbage file with a random file name with a .part extension of mime type application/x-trash. The contents of the file is that of the old index.html file.

Google searching has turned up nothing but a lone thread in these forums that has gone unanswered for the past several months.

How do I fix this behavior?

---

### Post by Lutrova on 2009-07-27
Since absolutely no one has bothered to try to respond to this post in the almost two months since this was posted, I thought I'd share my one and only "fix". Many different forums I had searched with a similar issue suggested fiddling with the mime types and such. Unfortunately none of that worked.

My own personal fix involved simply clearing the browser cache completely with which I was surfing with. Although this isn't exactly a sure fix for everyone (or even myself) since I have no idea why this fix worked or even why the problem occurred to begin with and therefore stands a chance this can happen again. Considering that this happened anyhow suggests a problem with Apache's configuration somewhere. It is also possible it was a bug in Firefox attempting to draw from a nonexistent file and was instead trying to download a .part file that was coming from its own cache of the original site. Since this originally happened in Firefox 3 it's difficult to tell especially since the release of the newer versions in recent times.

So to those of you having trouble with a similar issue, completely clear out all the history and browser cache of the web browser you were using to begin with. If the problem persists then it's likely either a bug or something in the configuration worthy of seeking further help over.

---

