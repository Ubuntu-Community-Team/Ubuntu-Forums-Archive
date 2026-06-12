---
title: "How to preserve battery by controlling the charge level?"
date: 2009-01-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vdobriakov on 2009-01-06
I typically use my notebook as follows:
* using at home at a power outlet
* close lid to switch the notebook to standby mode and drive to work, during this time the charge state goes down from 100% to 98%
* connect to outlet at the office - the notebook starts charging; so it wears the Li-Ion battery out

Sometimes I also need the notebook on travel, where I wish the full battery capacity. And it should be nearly the same in one or two years (as with my old Thinkpad).

Experts say, that modern Li-Ion batteries wear out quicker when they hold a large charge or are subject to higher temperatures. So they recommend to avoid charging if battery is nearly full, unless you will need its full capacity soon; keep it on the 30%-85% charged range. 

For my old IBM Thinkpad there was a special tp_smapi module (you had to compile it yourself) [http://www.thinkwiki.org/wiki/Tp_smapi](http://www.thinkwiki.org/wiki/Tp_smapi) Also see [http://ubuntuforums.org/showthread.php?t=546537](http://ubuntuforums.org/showthread.php?t=546537) But I did not find anything similar for my Dell XPS M1330. Is there any special kernel module or acpi setting for that?

It is unfortunate, that the default Ubuntu + Dell behaviour is to kill the battery as fast as possible. I do not think, they make a lot of money by selling new batteries and hope, that this is simply an oversight. BTW, does the Windows version have such a tool?

Best Regards,

Vladimir Dobriakov
[http://www.innoq.com/blog/vd](http://www.innoq.com/blog/vd)

---

### Post by blierp on 2009-01-07
this is one of the last major concerns i have with linux on my xps m1530; the battery drains much faster then in windows.

I would really like to see an easy to use tool to control this as opposed to all the complicated scripts that you have to use today.

---

### Post by hellmet on 2009-11-06
Yeah. There ought to be a generic battery threshold manager/tool in Ubuntu..[ Let's brainstorm it]("http://brainstorm.ubuntu.com/idea/22336/").

---

