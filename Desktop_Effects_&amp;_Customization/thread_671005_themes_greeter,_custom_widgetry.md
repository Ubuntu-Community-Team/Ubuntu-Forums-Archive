---
title: "themes greeter, custom widgetry"
date: 2008-01-18
forum: Desktop Effects &amp; Customization
---

### Post by bkhands on 2008-01-18
I followed the themes greeter' guide to setup a custom list in my <themes>.xml as foloow:

<item type="list" id="custom-config">
<pos anchor="c" x="50%" y="70%" width="50" height="200"/>
<listitem id="foo">
<text>Foo</text>
</listitem>
<listitem id="bar">
<text>Bar</text>
</listitem>
</item>

In Gnome Display Manager Reference Manual, it says I can find value(foo or bar in above case) in /var/lib/gdm/:0.GreeterInfo, but I can't find this dir. 

[B]here is what Gnome Display Manager Reference Manual says:
[/B]
9.2.11.&#8195;Custom Widgetry
          Currently there is one item which is customizable and this is
          the list item.  If you need to ask the user extra things, such as
          to pick from a list of places to log into, or set of custom login
          sessions you can setup the list item and add listitem children that
          describe the choices.  Each listitem must have an id and a text
          child.  The choice will be recorded in the file
          <ServAuthDir>/<display>.GreeterInfo
          as <list id>=<listitem id>.

          For example suppose we are on display :0,
          ServAuthDir is
          <var>/lib/gdm and we have the following in the
          theme:
 <item type="list" id="custom-config">
<pos anchor="nw" x="1" y="1" height="200" width="100">
<listitem id="foo">
<text>Foo</text>
</listitem>
<listitem id="bar">
<text>Bar</text>
</listitem>
</item>

Then if the user chooses 'Foo' then <var>/lib/gdm/:0.GreeterInfo will contain: custom-config=foo

**here is my fold contains: **

root@cgeng-desktop:/home/cgeng# cd /var/lib/gdm
root@cgeng-desktop:/var/lib/gdm# ls -la
total 28
drwxrwx--T  4 root gdm  4096 2008-01-17 12:54 .
drwxr-xr-x 79 root root 4096 2007-12-28 11:58 ..
-rw-r-----  1 root root   45 2008-01-17 12:54 :0.Xauth
-rw-r--r--  1 root root   64 2008-01-17 12:54 :0.Xservers
-rw-------  1 root root   33 2008-01-16 17:02 .cookie
drwxr-xr-x  2 gdm  gdm  4096 2007-10-31 11:35 .fontconfig
drwxr-xr-x  3 gdm  gdm  4096 2007-12-03 09:57 .gcin
prw-rw----  1 root root    0 2008-01-16 17:02 .gdmfifo

what happaned? Please help me!

---

