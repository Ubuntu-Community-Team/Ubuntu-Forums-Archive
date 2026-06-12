---
title: "Set default desktop to show thunderbird icon on panel rather than evolution?"
date: 2006-08-24
forum: Desktop Environments
---

### Post by xucchini on 2006-08-24
Hello, I really prefer that people use Thunderbird by default
rather than Evolution.

How would one set the system defaults so that when someone
first logs into an Ubuntu Dapper system that the Top Panel has
an icon that launches Thunderbird rather than Evolution.
(Assuming I have already used apt-get to install Thunderbird)

I did a gconftool-2 / --dump and see this section

    <entry>
      <key>/apps/panel/default_setup/objects/email_launcher/launcher_location</key>
      <schema_key>/schemas/apps/panel/objects/launcher_location</schema_key>
      <value>
        <string>evolution-mail.desktop</string>
      </value>
    </entry>


But not sure how to go about changing it properly.

Or perhaps there is a way I can easily edit a file containing this
config in xml or something?

---

### Post by peabody on 2006-08-24
I think you can just change evolution-mail.desktop shortcut to the shortcut for Thunderbird, which, while not knowing it but taking a wild guess, is probably thunderbird.desktop?

---

