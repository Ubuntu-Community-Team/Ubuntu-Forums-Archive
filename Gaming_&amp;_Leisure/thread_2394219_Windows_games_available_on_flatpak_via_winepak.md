---
title: "Windows games available on flatpak via winepak"
date: 2018-06-14
forum: Gaming &amp; Leisure
---

### Post by amauryat on 2018-06-14
One needs to add the winepak repository :

```
 flatpak remote-add --if-not-exists winepak [https://dl.winepak.org/repo/winepak.flatpakrepo](https://dl.winepak.org/repo/winepak.flatpakrepo)
```

These games already available :

 ```
~]$ flatpak remote-ls winepak
Ref                                     
com.blizzard.BattleNet.BaseApp          
com.blizzard.Overwatch                  
com.blizzard.StarCraft2                 
com.blizzard.WoW                        
com.leagueoflegends.Client              
com.oskarstalberg.Planet                
com.pathofexile.Client                  
com.worldoftanks.Client
```

---

### Post by oldrocker99 on 2018-06-14
Holy ":&&_$$-!


EDIT: This is what I got:
```
oldrocker99@oldrocker99-HP-EliteBook-8460p:~$ flatpak remote-ls winepak
Ref                                     
com.blizzard.BattleNet.BaseApp          
com.blizzard.Overwatch                  
com.blizzard.StarCraft2                 
com.blizzard.WoW                        
com.leagueoflegends.Client              
com.oskarstalberg.Planet                
com.pathofexile.Client                  
com.worldoftanks.Client                 
info.cemu.Cemu                          
org.notepad_plus_plus.Notepad-plus-plus 
org.winepak.Platform                    
org.winepak.Platform.Compat32           
org.winepak.Platform.Extension.corefonts
org.winepak.Platform.Extension.d3dx9    
org.winepak.Platform.Extension.msls31   
org.winepak.Platform.Extension.vcrun2010
org.winepak.Platform.Extension.vcrun2012
org.winepak.Platform.Extension.vcrun2013
org.winepak.Platform.Extension.vcrun2015
org.winepak.Platform.Wine               
org.winepak.Platform.Wine.Compat32      
org.winepak.Sdk                         
oldrocker99@oldrocker99-HP-EliteBook-8460p:~$ com.blizzard.StarCraft2
```

How do you download?](*,)

It took me a few tries, but I got it! Now I have Yet Another Racing Game I totally suck at!:(

---

### Post by amauryat on 2018-06-15
You install with flatpak command structure, for instance :
League of Legend :
```
 flatpak install winepak com.leagueoflegends.Client
```

world of warcraft :
```
 flatpak install winepak com.blizzard.WoW
```


--> [http://docs.flatpak.org/en/latest/using-flatpak.html](http://docs.flatpak.org/en/latest/using-flatpak.html)

---

### Post by thenailedone on 2018-06-15
Want to use your package manager to handle your flatpaks in Ubuntu?
```
sudo apt install gnome-software-plugin-flatpak
```

---

### Post by oldrocker99 on 2018-06-20
I used winepak to install Starcraft II, and it behaved fine, but I cannot find it anywhere in my system. 

WHERE are they installed?

---

### Post by thenailedone on 2018-06-23
> **oldrocker99 said:**
> I used winepak to install Starcraft II, and it behaved fine, but I cannot find it anywhere in my system. 

I was not so lucky to get it to work. Battlenet kept crashing (there seems to be some issues when running nvidia graphics and some of the drivers that get bundled with flatpaks).

---

