---
title: "firefox 2.0.13 can add addon&#347; - plse help"
date: 2008-04-04
forum: Desktop Environments
---

### Post by Rowanmf on 2008-04-04
I have been battling with adding addons to firefox for the last week , i wanted the video download helper addon , clicked the button to add it , it was downloaded , but when it starts installing it comes up with a error , plse see firefoxerror1.png attached - then looking in the error consol you see it gives a error installocation has no properties.see firefoxerror2.png
when this first happened , i emailed the developer and he said i should reload firefox , i used synaptic and marked firefox for re installation , did that , and it still came up with the same error , so i removed firefox completely , even did a reboot afterwards (yuck) just to make sure , then re installed fire fox , i have just finished doing that and it still comes up with the same error , this is driving me mad , i have tried several other addons and each of them comes up with the same error ... 

please can some one help 

Thanks 

Rowan

---

### Post by warp99 on 2008-04-04
First you don't need to reinstall Firefox because the add-ons do not work. All of your local settings are kept in you /home/$user/.mozilla/firefox directory. By removing and reinstalling Firefox you've just placed yourself back in the same position since the plug-ins are still there. I would suggest that you backup your bookmarks then delete your local Firefox directory:

```
rm -r ~/.mozilla/firefox
```

Firefox will generate a new directory once you reload your browser. Try to install the plug-ins again. If the plug-ins do not want to load then they are not compatible and you need to speak with the developers.

---

### Post by Rowanmf on 2008-04-04
well , that was perfect , did everything you said and it worked perfectly ... 

a thousand thanks 

Rowan

---

