---
title: "Choose desktop on load"
date: 2005-06-13
forum: Desktop Environments
---

### Post by andrewsawyer on 2005-06-13
Is it possible to choose what desktop a program loads into when it opens?

Previous to Ubuntu, I was using Mandrake (for a couple of weeks) and you have an option to right click on the programs menu bar and choose to save the settings.  It may have been a KDE thing rather than Mandrake - I don't know that much about it all.

I load Thunderbird and aMSN on boot each time I start my machine, however they always load in the first desktop (unless I quickly switch desktop before they load).  I would like them to load in the second desktop if possible each time, however I have yet to find a way to do it.  If anyone knows of a way to do it could they please let me know?

Also, can you save the dimensions and location of a program on a specific desktop, so Thunderbird always opens full screen minus some space on the right, and aMSN opens to the right of it each and every time?

If it's not something that is currently implemented, how would I go about suggesting it for future releases?

Thanks,

Andy

---

### Post by andrewsawyer on 2005-06-13
Update to this - I have found out about devil's pie (however I have no idea how to use it).

I found a preconfigured script to get Eterm to load on each workspace with no tilebar icon, however I would like to get Thunderbird and aMSN to load in Workspace 2, and I don't know how.

I have included the devilspie xml file below, and I run the two programs from the start up section is follows:

alltray -s amsn
alltray -s mozilla-thunderbird

.devilspie.xml file below

```
<?xml version="1.0"?>
<!DOCTYPE devilspie SYSTEM "devilspie.dtd">

<devilspie>
  <flurb name="Eterm pinned and no taskbar">
    <matchers>
       <matcher name="DevilsPieMatcherWindowName">
         <property name="application_name" value="Eterm"/>
       </matcher>
    </matchers>
<!-- The action below will pin Eterm to all workspaces-->
     <actions>
         <action name="DevilsPieActionSetWorkspace">
            <property name="pinned" value="TRUE"/>
      </action>
<!-- The action below will remove Eterm from the windows list and the Workspace Switcher (thanks Trash:)-->
      <action name="DevilsPieActionHide">
        <property name="skip_tasklist" value="TRUE"/>
        <property name="skip_pager" value="TRUE"/>
      </action>
     </actions>
</flurb>
</devilspie>
``` 

If anyone would be kind enough to show me how to put Thunderbird and aMSN into this so that they load in the second workspace then that would be great.

---

### Post by notepad on 2008-02-24
did you end up getting far with this?
devilspie now no longer uses xml and im trying to get it to manipulate amsn for me.

---

