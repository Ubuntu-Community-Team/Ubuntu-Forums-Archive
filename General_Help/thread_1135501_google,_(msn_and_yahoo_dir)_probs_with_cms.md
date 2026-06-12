---
title: "google, (msn and yahoo dir) probs with cms ?"
date: 2009-04-24
forum: General Help
---

### Post by posterreal1 on 2009-04-24
[FONT=Arial]i request help on this topic: MSN, Google and Yahoo Directory currently ignore on of my clients website. None of the other search engines seems to have trouble. [/FONT]
  
  [FONT=Arial]The index.html is already in the three above. From there on, a cms is called through a frameset looking like this:[/FONT]
  
  [FONT=Arial]frame top= /cgi-bin/cms.pl?template=start [/FONT]
  [FONT=Arial]frame bottom= /cgi-bin/cms.pl?template=foot [/FONT]
  
  [FONT=Arial]These two pages are searchable as well (along with index.html) in Google, MSN and Yahoo, but none of the following pages.[/FONT]
  
  [FONT=Arial]So, i have a total of three pages , while some hundred are waiting since november 2002. The sites deeplinks look like this:[/FONT]
  
  [FONT=Arial]<a href = /cgi-bin/cms.pl?template=article //for categories[/FONT]
  [FONT=Arial]<a href = /cgi-bin/cms.pl?template=article&id=1234 //for articles[/FONT]
  
  [FONT=Arial]I used webmasterplan.de with their "this is how your site looks to engines" tool and found out that this tool requires "=" to be replaced by "%3d" (ascii opcode for equal signs). is this the same for google and company ?[/FONT]

---

