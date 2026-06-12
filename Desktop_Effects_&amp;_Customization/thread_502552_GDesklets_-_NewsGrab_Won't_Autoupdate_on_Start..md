---
title: "GDesklets - NewsGrab Won't Autoupdate on Start."
date: 2007-07-16
forum: Desktop Effects &amp; Customization
---

### Post by coldstatue on 2007-07-16
I have to configure desklet, go into items, uncheck and check titles... Then they load. Still, I have to hover over the titles to get my fonts and color prefs to take hold. I found an old thread in the archives that said installing the old tarbal solved some update problems, but I am hoping this has been solved. I installed via apt-get.

When I do re-check titles, I get this error-

```
'NoneType' object is not callable                                                    
/home/coldstatue/.gdesklets/Displays/NewsGrab/newsgrab.script                        
  589                                   Dsp.time[i].value = item[i + pos][3]         
  590                                                                                
  591           refresh_arrows()                                                     
  592                                                                                
  593           if news.refresh == 1:                                                
> 594                   news.refresh = 0                                             
  595                   if wrap != width:                                            
  596                           set_wrap(width)                                      
  597                                                                                
  598                   update_actions()                                             
  599                   refresh_newsitems()                                          
  600                                                                                

```

line 594 is highlighted.

I have completely removed all traces of gdesklets and reinstalled. It didn't work. NewsGrab is my favorite RSS desklet, so I'd love to get this one working the way it is supposed to, though it is functional.

Thanks.

---

### Post by Presto123 on 2008-02-03
I have found the fix for this old issue.

Change the ```
news.refresh = 0 
```

to

```
news.refresh != 0 
```

Only issue now is that it occasionally freezes. Restart system seems to fix most of the issues here. I would also configure the desklet to your preferences before applying this change.

---

