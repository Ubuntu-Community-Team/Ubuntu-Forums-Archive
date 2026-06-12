---
title: "http forum icons cause &quot;insecure website&quot; warnings on various browsers"
date: 2020-08-20
forum: Forum Feedback &amp; Help
---

### Post by fluffy20470-50233 on 2020-08-20
Due to the fact that icons are loaded in plain http (for example, [http://ubuntuforums.org/images/icons/icon3.png](http://ubuntuforums.org/images/icons/icon3.png)) many browsers display a warning in the address bar that [https://ubuntuforums.org](https://ubuntuforums.org) is an insecure website. It would be nice if these icons were loaded as https by default.

---

### Post by deadflowr on 2020-08-20
*Thread moved to **Forum Feedback and Help***

Yeah, I think we've had this discussion somewhere before.

---

### Post by edwardmax on 2020-09-10
Yes, I read the solution on google support, any URL without the secure protocol it shows the same warning, so its better to use **https **on any website to avoid user botheration & no-doubt its has multiple benefits too.

---

### Post by EuclideanCoffee on 2020-09-10
Does the sys admin need help with this? I can volunteer my time to help sort out the root cause.

---

### Post by manpreetweb on 2020-09-10
You need to deploy SSL ([LEFT][COLOR=#111111][FONT=Arial]Secure Sockets Layer) on your website.  SSL is a [LEFT][COLOR=#111111][FONT=Arial]protocol that ensures the security of data sent through internet using encryption. [LEFT][COLOR=#111111][FONT=Arial]This should resolve the issue.[/FONT][/COLOR][/LEFT][/FONT][/COLOR][/LEFT][/FONT][/COLOR][/LEFT]

---

### Post by overdrank on 2020-09-10
I knew this issue had been going on for awhile.
[https://ubuntuforums.org/showthread.php?t=2264332](https://ubuntuforums.org/showthread.php?t=2264332)

---

### Post by 64bitguy2 on 2020-12-12
4- months seems like an excessive time to have broken https validation.

Someone needs to edit all the template files and fix them ... not rocket science, there is broken https compliance all over the place.

Examples:
/images/icons/ calls (icon1.png, icon2.png, icon3.png, etc...)

Javascript Popup Menus
Links to IRC Forum IRC Channel, Show forum groups, misc.php?do=showrules, and showgroups.php forum staff), etc...

For example, here is PART of the source of a main page...  Notice all of the "http" calls within it?  Those are _**all**_ non-compliant.
```
<ul class="floatcontainer">
                
                    
                        <li class="popupmenu" id="vbmenu_qlinks">
                            <a href="javascript://" class="popupctrl">Quick Links</a>
                            <ul class="popupbody popuphover">
                                
                                    <li id="vbclink_albums"><a href="album.php">Albums</a></li>
                                
                                    <li id="vbalink_settings"><a href="profile.php?do=editoptions">General Settings</a></li>
                                
                                    <li id="vbqlink_threads"><a href="subscription.php">Subscribed Threads</a></li>
                                
                                    <li id="vbalink_profile"><a href="profile.php?do=editprofile">Edit Profile</a></li>
                                
                                    <li id="vbclink_contacts"><a href="profile.php?do=buddylist">Friends & Contacts</a></li>
                                
                                    <li id="vbqlink_contacts"><a href="javascript://" onclick="window.open(getBaseUrl() + 'misc.php?do=buddylist&focus=1','buddylist','statusbar=no,menubar=no,toolbar=no,scrollbars=yes,resizable=yes,width=250,height=300'); return false;">Open Contacts Popup</a></li>
                                
                                    <li id="link_mja2_647"><a href="search.php?do=finduser&amp;userid=2154542&amp;starteronly=1& amp;contenttype=vBForum_Thread">Find all my threads</a></li>
                                
                                    <li id="link_mja2_130"><a href="search.php?do=finduser&amp;userid=2154542&amp;contenttype=vB Forum_Post&amp;showposts=1">Find all my posts</a></li>
                                
                                    <li id="link_mje2_914"><a href="search.php?do=process&type[]=1&replyless=1&replylimit=0">Unanswered Posts</a></li>
                                
                                    <li id="link_mjm0_271"><a href="search.php?do=getnew&contenttype=vBForum_Post">New Posts</a></li>
                                
                                    <li id="link_odiw_103"><a href="http://ubuntuforums.org/showgroups.php">View Forum Leaders</a></li>
                                
                                    <li id="link_mdy0_388"><a href="http://ubuntuforums.org/faq.php">FAQ</a></li>
                                
                                    <li id="link_nzqx_135"><a href="http://ubuntuforums.org/faq.php?faq=vb3_reading_posting#faq_vb3_contact_admin">Contact an Admin</a></li>
                                
                            </ul>
                        </li>
                    
                
                    
                        <li class="popupmenu" id="menu_mja2_174">
                            <a href="javascript://" class="popupctrl">Forum Community</a>
                            <ul class="popupbody popuphover">
                                
                                    <li id="link_mja2_178"><a target="_blank" href="https://wiki.ubuntu.com/ForumCouncil">Forum Council</a></li>
                                
                                    <li id="link_mja2_759"><a target="_blank" href="https://wiki.ubuntu.com/ForumCouncilAgenda"><span> FC Agenda</span></a></li>
                                
                                    <li id="link_mja2_602"><a target="_blank" href="https://wiki.ubuntu.com/ForumsGovernance">Forum Governance</a></li>
                                
                                    <li id="link_ntk3_139"><a href="http://ubuntuforums.org/showgroups.php/">Forum Staff</a></li>
                                
                                    <li id="link_mja2_802"><a href="http://ubuntuforums.org/misc.php?do=showrules">Ubuntu Forums Code of Conduct</a></li>
                                
                                    <li id="link_mja2_447"><a target="_blank" href="http://webchat.freenode.net/?channels=ubuntuforums">Forum IRC Channel</a></li>
                                
                            </ul>
                        </li>
                    
                
                    
                        <li class="popupmenu" id="menu_mja2_686">
                            <a href="javascript://" class="popupctrl">Ubuntu Community</a>
                            <ul class="popupbody popuphover">
                                
                                    <li id="link_mja2_167"><a target="_blank" href="http://community.ubuntu.com/">Ubuntu</a></li>
                                
                                    <li id="link_mja2_232"><a target="_blank" href="http://www.ubuntu.com/download/desktop">Get <b style="color: #dd4814">Ubuntu</b></a></li>
                                
                                    <li id="link_mja2_426"><a target="_blank" href="http://www.kubuntu.org/getkubuntu">Get <b style="color:#10147e">Kubuntu</b></a></li>
                                
                                    <li id="link_mja2_138"><a target="_blank" href="http://xubuntu.org/getxubuntu/">Get <b style="color: #04a">Xubuntu</b></a></li>
                                
                                    <li id="link_mja2_351"><a target="_blank" href="https://lubuntu.me/downloads/">Get <b style="color: #033C71">Lubuntu</b></a></li>
                                
                                    <li id="link_nzmw_867"><a target="_blank" href="http://ubuntustudio.org/download/">Get <b style="color:#116286">Ubuntu Studio</b></a></li>
                                
                                    <li id="link_nzmw_456"><a target="_blank" href="http://www.mythbuntu.org/download-type">Get <b style="color: #dd4814">Mythbuntu</b></a></li>
                                
                                    <li id="link_nzmw_464"><a target="_blank" href="http://www.edubuntu.org/download">Get <b style="color: #a30b00">Edubuntu</b></a></li>
                                
                                    <li id="link_nzmw_559"><a target="_blank" href="http://ubuntugnome.org/download/">Get <b style="color: #dd4814">Ubuntu GNOME</b></a></li>
                                
                                    <li id="link_nzmw_633"><a target="_blank" href="http://www.ubuntukylin.com/downloads/show.php?lang=en&id=122">Get <b style="color: #dd4814">Ubuntu Kylin</b></a></li>
                                
                                    <li id="link_nzy1_643"><a target="_blank" href="https://ubuntubudgie.org/downloads">Get <b style="color: #8B008B">Ubuntu Budgie</b></a></li>
                                
                                    <li id="link_nzy1_968"><a target="_blank" href="https://ubuntu-mate.org/download/">Get <b style="color: #87A556">Ubuntu Mate</b></a></li>
                                
                                    <li id="link_mja2_877"><a target="_blank" href="http://www.ubuntu.com/project/about-ubuntu/conduct">Ubuntu Code of Conduct</a></li>
                                
                                    <li id="link_mja2_199"><a target="_blank" href="https://wiki.ubuntu.com/">Ubuntu Wiki</a></li>
                                
                                    <li id="link_mja2_891"><a target="_blank" href="https://help.ubuntu.com/community/">Community Wiki</a></li>
                                
                            </ul>
                        </li>
                    
                
                    
                        <li class="popupmenu" id="menu_mja2_593">
                            <a href="javascript://" class="popupctrl">Other Support</a>
                            <ul class="popupbody popuphover">
                                
                                    <li id="link_mja2_994"><a target="_blank" href="https://answers.launchpad.net/">Launchpad Answers</a></li>
                                
                                    <li id="link_mja2_430"><a target="_blank" href="http://webchat.freenode.net/?channels=ubuntu">Ubuntu IRC Support</a></li>
                                
                                    <li id="link_mja2_646"><a target="_blank" href="http://askubuntu.com">AskUbuntu</a></li>
                                
                                    <li id="link_mja2_817"><a target="_blank" href="https://help.ubuntu.com">Official Documentation</a></li>
                                
                                    <li id="link_mja2_745"><a target="_blank" href="https://help.ubuntu.com/community">User Documentation</a></li>
                                
                            </ul>
                        </li>
                    
                
                    
                        
                            <li id="vbflink_pms"><a target="_blank" href="private.php">Private Messages</a></li>
                        
                    
                
                    
                        <li class="popupmenu" id="menu_mtaz_185">
                            <a href="javascript://" class="popupctrl">Social Media</a>
                            <ul class="popupbody popuphover">
                                
                                    <li id="link_mtaz_522"><a target="_blank" href="https://www.facebook.com/UbuntuForums">Facebook</a></li>
                                
                                    <li id="link_mtaz_149"><a target="_blank" href="https://twitter.com/ubuntuforums">Twitter</a></li>
                                
                            </ul>
                        </li>
                    
                
                    
                        <li class="popupmenu" id="menu_ode5_930">
                            <a href="javascript://" class="popupctrl">Useful Links</a>
                            <ul class="popupbody popuphover">
                                
                                    <li id="link_ode5_240"><a target="_blank" href="http://distrowatch.com/table.php?distribution=ubuntu">Distrowatch</a></li>
                                
                                    <li id="link_ode5_738"><a target="_blank" href="https://bugs.launchpad.net/ubuntu/">Bugs: Ubuntu</a></li>
                                
                                    <li id="link_ode5_821"><a target="_blank" href="https://launchpad.net/ubuntu/+ppas">PPAs: Ubuntu</a></li>
                                
                                    <li id="link_ode5_923"><a target="_blank" href="http://www.webupd8.org/">Web Upd8: Ubuntu</a></li>
                                
                                    <li id="link_ode5_916"><a target="_blank" href="http://www.omgubuntu.co.uk/">OMG! Ubuntu</a></li>
                                
                                    <li id="link_ode5_248"><a target="_blank" href="https://insights.ubuntu.com/">Ubuntu Insights</a></li>
                                
                                    <li id="link_ode5_244"><a target="_blank" href="http://planet.ubuntu.com/">Planet Ubuntu</a></li>
        
```

Basically what I'm saying here is... **_all_** of your Vbulletin templates need to be looked over and everywhere that has a static link to http needs to be replaced with https.

The easiest way to see the non-compliant links is to simply view the source code of every main template page.... the majority of them jump right out at you.  The rest are found right in the template definitions themselves.  This isn't rocket science... someone just needs to follow the same steps they would for general W3C page validation compliance testing.

Just so were are all on the same page, this has nothing to do with SSO or certificates, it is entirely about embedded functions and calls.  What you can't fix in templates themselves will be found in the Java/javascript code that is called by them or embedded in static DB URL definitions.

etc...

This must be considered as a _**serious security issue**_ as the broken https compliance means that Vbulletin forums is creating a **_major_** security hole that hackers can (and yes... as well documented, often do) exploit to penetrate sessions and that can be used not only to compromise forums data itself; but user Ubuntu's SSO security as well and thus [COLOR=#ff0000]**all UbuntuOne accounts AND data throughout UbuntuOne universe is at risk**[/COLOR] and that kind of threat _should not be ignored_ for one day, never mind 4-months, for obvious reasons.

This kind of thing is exactly what cross-site scripting attacks exploit.  This is a one-day fix for someone that knows what they are doing with Vbulletin and W3C template validation and should not be ignored any longer for the major security reasons I have outlined.

---

### Post by TheFu on 2020-12-12
Nobody posting here controls the servers.  Canonical controls them.

OTOH, Firefox isn't complaining - perhaps it complained long ago and I told it to stop?
Unfortunately, dillo and lynx do not work here.

---

### Post by 64bitguy2 on 2020-12-12
> **TheFu said:**
> Nobody posting here controls the servers.  Canonical controls them.

OTOH, Firefox isn't complaining - perhaps it complained long ago and I told it to stop?
Unfortunately, dillo and lynx do not work here.

I'm sure Canonical controls their servers.  I'm also sure they have someone assigned to be responsible for Vbulletin oversight (site administrator) to maintain code and controls.

As for Firefox "complaining", it "complains" on every single non-compliant page.

If you go up one level to: [https://ubuntuforums.org/forumdisplay.php?f=48](https://ubuntuforums.org/forumdisplay.php?f=48), you will find Firefox will "complain" because the "forumdisplay" template is non-compliant.  The "showthread" template appears to be compliant because for example, I can add an explanation point icon to this forum topic and it does not break compliance.

In addition to template compliance... again.. static links need to be updated too... (there's just no excuse for not doing it).  Everything in here for example.... which is called by every template.
[IMG]https://i.postimg.cc/TPYBHQQK/Screenshot-from-2020-12-12-15-03-53.png[/IMG]

---

