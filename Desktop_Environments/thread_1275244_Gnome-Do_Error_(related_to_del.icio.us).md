---
title: "Gnome-Do Error (related to del.icio.us)"
date: 2009-09-25
forum: Desktop Environments
---

### Post by ProfBib on 2009-09-25
I use and really like Gnome-Do.  Today, I logged into my office machine and Gnome-Do (which starts automatically at login) would not respond the the usual keyboard shortcut.  In system monitor, I discovered that it wasn't running, so I tried to start it from within a terminal and got this output:

> Delicious.BookmarksItemSource "Del.icio.us bookmarks" encountered an error in Items: Argument cannot be null.
Parameter name: source.
Delicious.BookmarksItemSource "Del.icio.us bookmarks" encountered an error in Items: Argument cannot be null.
Parameter name: source.

Unhandled Exception: System.Xml.XmlException: unexpected end of file in an attribute value  Line 104, position 701.
  at Mono.Xml2.XmlTextReader.ReadAttributeValueTokens (Int32 dummyQuoteChar) [0x00000] 
  at Mono.Xml2.XmlTextReader.ReadAttributes (Boolean isXmlDecl) [0x00000] 
  at Mono.Xml2.XmlTextReader.ReadStartTag () [0x00000] 
  at Mono.Xml2.XmlTextReader.ReadContent () [0x00000] 
  at Mono.Xml2.XmlTextReader.Read () [0x00000] 
  at System.Xml.XmlTextReader.Read () [0x00000] 
  at Delicious.Delicious.UpdateBookmarks () [0x00000] 
Looks like there is a problem with the del.icio.us plugin.  Has anyone else exprienced this?  Any idea how to fix it?  If I could get Gnome-Do started, I would just disable that plugin, but I can't even get it going.

Thanks,
Evan

---

### Post by ProfBib on 2009-09-25
Temporary Fix:

Edit:

~/.local/share/gnome-do/plugins-0.8.1.3/addin-db-001/config.xml

adding this line to that addins config file (config.xml) allowed me to disable the del.icio.us plugin and get things running again:

    <Addin id="Do.delicious,2.0" enabled="False" />

So, my config file looks something like this:

<Configuration>
  <AddinStatus>
    <Addin id="Do.RememberTheMilk,1.0" enabled="False" />
    <Addin id="Do.delicious,2.0" enabled="False" />
  </AddinStatus>
</Configuration>

Please let me know if you hear of an update to this plugin, and have a wonderful weekend!

Cheers,
Evan

---

