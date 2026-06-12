---
title: "Request for third party Libs section."
date: 2006-09-19
forum: Forum Feedback &amp; Help
---

### Post by Omnios on 2006-09-19
Hi hi again. Over the last few months I have been playing with non synaptic packages which require a lot of libs from elf or even external libs and have discovered a huge void in this respect. FOr example this is the history of a Xlibs package which a lot of external prorgrams require. 

```

Bug #60823:              **Please backport xlibs dummy package.deb.**

                                                                                      function toggleFormVisibility(row) {     if (row.style.display=="none") {       row.style.display = "table-row";     } else {       row.style.display = "none";     }     return false;   }                  Affects       Status       Importance       Assigned To                                                         [dapper-backports (upstream)]("https://launchpad.net/products/dapper-backports/+bug/60823/+editstatus")                                Rejected        Untriaged                                                              —                                                                                                                              Product           
                                     ([Choose…]("javascript:popup_window('@@popup-window?vocabulary=Product&field=field.product','500','400')")) 
                                                    Status         
                   Importance         
                                  Unconfirmed Needs Info Rejected Confirmed In Progress Fix Committed Fix Released  
  

        Untriaged
                                                    Assigned to         
                                    Nobody      
             Me           
               ([Choose…]("javascript:popup_window('@@popup-window?vocabulary=ValidAssignee&field=field.assignee','500','400'); document.getElementById('field.assignee').onkeypress()"))     
                   
        Comment on most recent change            *Backports packages must come from Edgy.*     
   
               Comment on this change (optional)            
        
           
  
                           [RIGHT]    Also affects:          [IMG]https://launchpad.net/@@/add[/IMG]       [         Upstream…       ]("https://launchpad.net/products/dapper-backports/+bug/60823/+upstreamtask")              [IMG]https://launchpad.net/@@/add[/IMG]       [         Distribution…       ]("https://launchpad.net/products/dapper-backports/+bug/60823/+distrotask")     [/RIGHT]
           Description ([edit]("https://launchpad.net/products/dapper-backports/+bug/60823/+edit"))      [FONT=monospace]This started off as a bug report of a missing xlibs dummy package which made it hard or impossible to install a lot of extra packages from sourceforge and newver versions of packages. However I found a xlibs dummy package deb posted on the forum.
 Quote[]
(untriaged) [Bug #60649]("https://launchpad.net/bugs/60649"):
no dummy package for xlibs giving dep error
Affects 	Status 	Importance 	Assigned To
xorg (Ubuntu) 	Rejected 	Untriaged 	—
Package
(Choose…)
Status 	Importance
 Untriaged
Assigned to
Nobody
Me
(Choose…)
Comment on most recent change
(none)
Comment on this change (optional)
Also affects: + Upstream… + Distribution…
Description (edit)
 Binary package hint: xlibs
 Hi I noticed that xlibs-deb has a dummy transitional package but there is not one for xlibs. From the amount of xlib arrors happening it seems that a xlibs dummy package was over looked for dapper. Please look into this.
  also when trying to download xlibs I get this error
 tom@miko:~$ sudo apt-get install xlibs
Reading package lists... Done
Building dependency tree... Done
Package xlibs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libxft1 xkeyboard-config
E: Package xlibs has no installation candidate
 Edit :::"'Solved with a Community member dummy package."
This description was updated. View original description.
Re: [[Bug 60649]("https://launchpad.net/bugs/60649")] no dummy package for xlibs giving dep error from Dennis Kaarsemaker at 2006-09-16 00:16:16 UTC
  status Rejected
 No Ubuntu application depends on this package so it's not needed. 3rd
party software should be fixed by those 3rd parties.
Solved by Community, User made dummy pacakage from Tomasz Witko at 2006-09-16 21:55:27 UTC
  Hi I found a solution on the Ubuntu forum found this dummy package from a users post. Thanks to user: PsYsK8eR
[http://ubuntuforums.org/attachment.php?attachmentid=11386&d=1150598009](http://ubuntuforums.org/attachment.php?attachmentid=11386&d=1150598009)
Re: no dummy package for xlibs giving dep error from Tomasz Witko at 2006-09-16 21:57:16 UTC
     * xlibs dummy package.
Quote[/]
  Please backport or include into repositories as it may solve a lot of problems people are having with external installs.
[/FONT]
             [CENTER]        [/CENTER]
                       [     **Re: Please backport xlibs dummy package.deb.**     ]("https://launchpad.net/products/dapper-backports/+bug/60823/comments/1")      from [Tomasz Witko]("https://launchpad.net/people/witko")     at 2006-09-16 22:42:22 UTC   
         [LIST]
[*]         [xlibs dummy .deb]("http://librarian.launchpad.net/4291021/xlibs_dummy.zip")[/LIST]               
  
                    [     **Re: Please backport xlibs dummy package.deb.**     ]("https://launchpad.net/products/dapper-backports/+bug/60823/comments/2")      from [John Dong]("https://launchpad.net/people/jdong")     at 2006-09-19 14:34:51 UTC   
               [FONT=monospace]Backports packages must come from Edgy.
[/FONT]
         
  
            [[IMG]https://launchpad.net/@@/treeCollapsed[/IMG]]("https://launchpad.net/products/dapper-backports/+bug/60823/+index#")[]("https://launchpad.net/products/dapper-backports/+bug/60823/+index#")

```

 Anyways there are lots of external packages that require xlibs but will not install without the dummy package. What I am getting at here is that because things do not break with Ubuntu packages they will not add the dummy package. Because it is not in Edgy they will not backport it so currently there is no Ubuntu support for a solution for the problem because it is third party. 

 Now that being said it might be interesting to have a third party lib section to have these fixes archived and searchable in the forums. Also this might be expanded with a third party lib and how to section. 

 I feel this would be highly supported by many users and solve a lot of present and furure probles. From the last release  *learnt that most of the libs require magore updating after about six months so this may be a band aid for the futire.*

---

