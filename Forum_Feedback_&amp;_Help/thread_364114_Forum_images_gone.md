---
title: "Forum images gone"
date: 2007-02-17
forum: Forum Feedback &amp; Help
---

### Post by tribble222 on 2007-02-17
This is a strange problem and I can't figure it out.  It started about two weeks ago.  After a month of the forum working perfectly, suddenly one day everything was white.  Most of the images were not being loaded ([see screenshot here](http://tribble222.com/ebay/forumscreen.jpg)).

I tried disabling all my extensions, installing swiftfox, reinstalling firefox through synaptic.  Nothing worked.  Finally I created a completely fresh firefox profile, and it then it worked!

"great!" I think, "now I can add in my extensions one by one and find the culprit!"  Well, I added in my extensions and the problem never came back.  I imported my old preferences and still it didn't come back.  So, I've just been using that new profile, which as far as I could tell was identical to my old one, except the forum rendered correctly.  So I was happy.

Today (about 5 days later) it suddenly stopped rendering correctly again in the middle of a browsing session.  I had a few tabs open of different forum pages at the same time, and suddenly one of the new tabs had the no images problem.  I could refresh (F5) the old tabs and they worked fine but if I went to any new forum link, the problem occurred.

Since I had a working tab and a non-working tab of the same page, I decided to compare the source to see what was up.  Going to view-->source showed they both have identical source.  But if I went to file-->save page and compared the source then, there are some differences.  For example, the good page would have

```
<script type="text/javascript"> vbmenu_register("usercpoptions"); </script> <img alt="" title="" src="good_files/menu_open.gif" border="0"></td>
```

but the bad page would have

```
<script type="text/javascript"> vbmenu_register("usercpoptions"); </script> <img alt="" title="" src="good_files/menu_open_002.gif" border="0"> <img alt="" title="" src="good_files/menu_open.gif" border="0"></td>
```

Or, the good page would have 

```
      <td style="cursor: pointer;" id="usercpoptions" class="ubuntu_navbar"><a href="http://ubuntuforums.org/usercp.php">User CP</a>
        <script type="text/javascript"> vbmenu_register("usercpoptions"); </script> <img alt="" title="" src="good_files/menu_open.gif" border="0"></td>
```

and the bad page would have

```
<td id="usercpoptions" class="ubuntu_navbar"><a href="http://www.ubuntuforums.org/usercp.php">User CP</a>
        <script type="text/javascript"> vbmenu_register("usercpoptions"); </script></td>
```

I have no idea what could be causing this to happen.  All other vbulletin sites render perfectly (as does the rest of the web).  I've spent hours searching for other people with my problem but apparently it's just me.  Does anyone have any idea what is going on?

---

### Post by tribble222 on 2007-02-19
...and tonight, for absolutely no reason, it started working again!  Strange.  This morning it didn't work but tonight it does.  Oh well.

---

