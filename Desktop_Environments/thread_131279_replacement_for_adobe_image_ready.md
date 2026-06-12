---
title: "replacement for adobe image ready"
date: 2006-02-16
forum: Desktop Environments
---

### Post by syklitengutt on 2006-02-16
Is there an replacement for adobe image ready?
F.ex. if I create a webdesign in gimp, is there a prog where I can slice the image
and add effects like mouse-over and then export it as html?

---

### Post by rem on 2006-02-16
Hey,

A while ago, I was asking myself the same thing about slicing and rollovers and I found out that actually you can do both using GIMP only.

The slicing method in GIMP isn't as advanced as it is in Image Ready, Photoshop or Fireworks but it can get the job done and this is the most important issue.

You can slice by dragging guides around wherever you need to crop then right click to Image/Transform/Guillotine. This will “cut” your picture along your guides, without altering the original. Save whatever slices you need for your project and that's it. Another method would be with plugins (filters) like [Perl-O-Tine]("http://registry.gimp.org/plugin?id=427") or Py-Slice, Perl and Python based, very easy to install and utilize (reffer to the [GIMP manual]("http://docs.gimp.org/en/concepts-intermediate.html#gimp-plugins-install")). This filters are pretty much alike. You have the option to choose the folder where the images will be saved, the images type and you'll have the HTML output also.

Regarding the rollovers, [here's a link]("http://libre.cyriacrea.net/roll/") to the rollover generator plugin I'm successfully using. You'll find links for download and tutorials in there.

Hope this will help. Maybe some others more experienced GIMP users could let us know about even easier methods on the above... ;)

---

