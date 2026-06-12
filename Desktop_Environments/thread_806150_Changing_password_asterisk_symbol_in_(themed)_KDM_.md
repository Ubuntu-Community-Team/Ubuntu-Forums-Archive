---
title: "Changing password asterisk symbol in (themed) KDM greeter?"
date: 2008-05-24
forum: Desktop Environments
---

### Post by Zorael on 2008-05-24
I have a screen resolution where the password asterisk at the KDE login screen becomes a big round blob, whereas on the Live CD when the resolution was lower I had a neat little centered dot. I'd like to get that dot, or any other symbol or sign instead of the blob. This is on a Kubuntu 8.04 installation.

I've tinkered around with both theme .xmls and **/etc/kde3/kdm/kdmrc**. The themes I have don't seem to define any fonts for the entry field, which was kind of surprising. See the code snippets below for the relevant sections of said themes. I tried adding **font="Sazanami Mincho 8"** (easy to see if I succeeded) to various tags to see if it accepted it, but I had no luck.

kdmrc has an option to change the standard font for the whole greeter (**StdFont**), which sadly also targets the user list. Further, it doesn't change the asterisk blob, even when supplying a unicode font. It seems to be theme and font independent?

kdmrc also doesn't seem to listen to the EchoMode setting; it defaults to OneStar and doesn't listen to anything else. I had hoped I could enter another symbol there and have it use it instead (a normal dash would be much preferrable to the current blob), only to find it's ignored.


```
*(circles theme: no font definitions)*

        <item type="rect">
	<normal color="#FF80FF" alpha="0.0"/>
	<pos anchor="w" y="50%" width="box" height="box"/>
        <box orientation="vertical" xpadding="0" ypadding="0" spacing="10">
    		  <item type="entry" id="user-entry">
            <pos anchor="n" x="50%" height="24" width="150"/>
    		  </item>
    		  <item type="entry" id="pw-entry">
            <pos anchor="n" x="50%" height="24" width="150"/>
    		  </item>
        </box>
```
```
*(kubuntu userlist theme: no font definitions)*

					<item type="rect" >
						<normal alpha="0.0" color="#cccccc" />
						<pos width="box" y="50%" anchor="w" height="box" />
						<box xpadding="0" spacing="10" ypadding="0" orientation="vertical" >
							<item type="entry" id="user-entry" >
								<pos width="130" x="50%" anchor="n" height="21" />
							</item>
							<item type="entry" id="pw-entry" >
								<pos width="130" x="50%" anchor="n" height="21" />
							</item>
						</box>
					</item>
```

Any ideas? A theme .xml solution would be awesome, but a kdmrc one would do just as well.

Thanks.

---

### Post by Zorael on 2008-05-27
Shameless bump.

---

