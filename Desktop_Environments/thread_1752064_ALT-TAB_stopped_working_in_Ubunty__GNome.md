---
title: "ALT-TAB stopped working in Ubunty / GNome"
date: 2011-05-07
forum: Desktop Environments
---

### Post by schworak on 2011-05-07
I had my ALT-TAB working just fine and yesterday for some reason, it just up and quit. I suspected COMPIZ but couldn't figure out thy it would have caused it to break.

I searched the web and found several forum entries and they all referenced the keybindings found in System > Preferences > Keyboard Shortcuts. These values were set for me but still no switching worked. But for some, these were disabled and setting them fixed their issues.

Move between windows, using a popup window
Move between windows immediately

Because these were already set for me, I thought back to the COMPIZ idea and decided to create a new profile using System > Preferences > Advanced Desktop Settings > Preferences.

I created the new profile which was automatically activated when I flicked the ADD button. I was surprised to get logged out without warning, but once I logged back in, my ALT-TAB was working again.

None of the other articles I read referenced this method so I wanted to share both methods here in one spot in case others were searching for the same solution.

Hope this info helps!

---

### Post by Copper Bezel on 2011-05-07
If I can add - if you're using Compiz, then the shortcut in Keyboard Shortcuts for window switching doesn't have any effect, because it's a binding for Metacity. Alt+Tab is provided by one of a few Compiz plugins like the Static Switcher and the Ring Switcher. It sounds like you'd accidentally disabled the plugin or changed the binding, then effectively reverted Compiz to default settings.

---

