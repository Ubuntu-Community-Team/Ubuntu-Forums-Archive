---
title: "KQ codes?  Cheats?  Walkthroughs? Help"
date: 2008-04-24
forum: Gaming &amp; Leisure
---

### Post by thrasher6900 on 2008-04-24
So I'm playing this KQ final fantasy like game.

But I'll admit, I like to cheat a little(money mainly) to get a leg up and move things along faster.

I was wondering if anybody had any information on this game.


I tried googeling it and it just comes up with "Kings Quest" and every potential link isn't valid and takes you to spam :|

I'll appreciate your input. . . ....unless of course you decide to be all moral and post stupid comments like "just play it normally blah blah blah you suck for cheating blah"

---

### Post by SomebodyElse on 2008-04-24
Which one? There are 8 games in the series, and there is an official remake of Kings Quest I as well as unofficial VGA remakes of games I-IV.

There are links to walkthroughs for the originals on this page:
[http://www.angelfire.com/ga/kingsquests/](http://www.angelfire.com/ga/kingsquests/)

---

### Post by scragar on 2008-04-24
I'm sure he's refering to the one installed via the repo's, not the old point and click games thay used to be sold on floppies.
```
apt-cache showpkg kq
```
I'm afraid I don't know of any cheats for it though.

---

### Post by SomebodyElse on 2008-04-24
> **scragar said:**
> I'm sure he's refering to the one installed via the repo's, not the old point and click games thay used to be sold on floppies.
```
apt-cache showpkg kq
```
I'm afraid I don't know of any cheats for it though.

Ah, now I feel dumb. 
Interesting game.

---

### Post by oki_180sx on 2008-04-25
intall "scanmem" via
apt-get install scanmem

open terminal while KQ is running
> pidof kq
remember the number it gives you

now
> scanmem
pid kq's pid
number of how much gold you have


it will scan for that value that you input
so buy something, then search for your amount of gold you have now
once it narrows it down to one result, the type
set "value of gold you want"

---

### Post by NHmomma on 2008-04-29
Hi,

I was going to start a new thread, but maybe if I post as part of this one, someone could help.

I recently downloaded this one, and have attempted to play a bunch of times, but for some reason, I cannot seem to save my game.  The menue comes up with save grayed out.  I thought maybe if I just got farther then I could save, but I have made it all the way to getting a second adventurer with me in the second city, and still no save option...  Getting tired of having to keep hitting the space bar through the beginning stuff...

Any suggestions?

---

### Post by magikx21 on 2008-04-30
KQ will not let you save anywhere. It is similar to Final Fantasy where you have to save when your on the world map or at specific save points.

---

### Post by thrasher6900 on 2008-06-15
> **scragar said:**
> I'm sure he's refering to the one installed via the repo's, not the old point and click games thay used to be sold on floppies.
```
apt-cache showpkg kq
```
I'm afraid I don't know of any cheats for it though.

I have the one that was in synaptic.

Is that the first one?

How do I get the others?:confused:

---

### Post by acoustibop on 2008-06-15
[KQ Lives]("http://kqlives.sourceforge.net/")

---

### Post by FranMichaels on 2008-06-15
> **oki_180sx said:**
> intall "scanmem" via
apt-get install scanmem

open terminal while KQ is running

remember the number it gives you

now


it will scan for that value that you input
so buy something, then search for your amount of gold you have now
once it narrows it down to one result, the type
set "value of gold you want"

You absolutely rock!
This is very cool. And it lets you do searches based on greater or lesser than (where you don't know the actual value, i.e. some sort of solid life bar or a change in position) it is just as powerful as the cheat engines in zsnes and mednafen. (even though it has more potential in terms of debugging, but that's over my head :) )

:guitar:

I never even knew scanmem existed, very intuitive too (got to love the help command)

EDIT: So so cool! Just changed my "zenny" to 99,999 in Breath of Fire III under PCSX. :D Eep... love scanmem!

---

### Post by noobmike on 2009-02-23
> **NHmomma said:**
> Hi,

I was going to start a new thread, but maybe if I post as part of this one, someone could help.

I recently downloaded this one, and have attempted to play a bunch of times, but for some reason, I cannot seem to save my game.  The menue comes up with save grayed out.  I thought maybe if I just got farther then I could save, but I have made it all the way to getting a second adventurer with me in the second city, and still no save option...  Getting tired of having to keep hitting the space bar through the beginning stuff...

Any suggestions?
You have to be out in the main screen (Not in a town) press esc+alt simultaniously and you will be able to save

---

### Post by octesian on 2009-02-24
Does anyone else have a problem trying to get sound to work?

---

### Post by Skinik on 2009-04-26
Can anyone please help me?  I have killed the dark imp in the tunnel, but he is still there blocking the way!!!

---

### Post by ultrasteeloid on 2009-09-03
I put in scanmem pid kq's pid 200
and then scanmem pid kq's pid 50.
But it said error: invalid pid specified.
What do you mean by searching for the number?:confused:

---

### Post by Chronon on 2009-09-03
> **scragar said:**
> I'm sure he's refering to the one installed via the repo's, not the old point and click games thay used to be sold on floppies.
.

The old version was keyboard only, no mouse.  You had to type in the actions that you wanted to try (e.g. climb tree, play flute, etc.).  I liked it because it made you think more creatively instead of just randomly clicking around to activate an action.  I was a bit disappointed when they went away from this to the point and click interface.

P.S. Sorry to not be any help with the problem. . .

---

### Post by BoyOfDestiny on 2009-09-03
> **ultrasteeloid said:**
> I put in scanmem pid kq's pid 200
and then scanmem pid kq's pid 50.
But it said error: invalid pid specified.
What do you mean by searching for the number?:confused:

Make sure you have kq running, then in terminal
```
scanmem `pidof kq`
```

Now with scanmem loaded it should show something like this
info: 76 suitable regions found.
Please enter current value, or "help" for other commands.
0> 

Now for this example, go into a battle.
Enter the value of your current hp into scanmem, hit enter.

Click kq, get hit, enter this value in scanmem.

Repeat. Each time it will narrow the search result.

I narrowed it to two results. One of them is the value you need to change (there are 2 because 1 is the value of the number drawn on the screen, the other the actual amount of hp or could just be some other thing in memory with the same value I guess...)

So the first slot is 0, in scanmem type

set 0 99

hit enter.

There, the hp is changed. If the value you enter is greater than max hp, it will just restore the health to max.

You get the idea now, you could find the value of gold in a shop, as you buy and sell items, and can re-set the values when you need more money and health, or have scanmem poke it in for you. Same goes for HP/MP, and if you mess around x,y cooridinates, and some values are next to each other (i.e. hp and max hp might be adjacent...)

Hope my explanation was okay, here is some screen shots of it in action...
(to make them a bit smaller they are indexed-color)

---

### Post by erikthedrink on 2009-09-30
The PID changes every time you play kq.  When the game window is open.  Shift the game window to one side of the screen.  Open a terminal and use the bottom right corner to resize the terminal.  Place the terminal on the other side of the screen without overlapping.  If you are in fullscreen mode in kq's game confiq, leave it.  In the terminal type in pidof kq  --- you should get the current assigned pid value.  Then type scanmem, then a space, then the current pid number you have just obtained, then a space, and then the value of the number you are trying to modulate.  If you choose zero, it will take some time and generate between 30 and 31 million matches.

---

### Post by comicman100 on 2009-10-20
> **NHmomma said:**
> Hi,

I was going to start a new thread, but maybe if I post as part of this one, someone could help.

I recently downloaded this one, and have attempted to play a bunch of times, but for some reason, I cannot seem to save my game.  The menue comes up with save grayed out.  I thought maybe if I just got farther then I could save, but I have made it all the way to getting a second adventurer with me in the second city, and still no save option...  Getting tired of having to keep hitting the space bar through the beginning stuff...

Any suggestions?
ok so you when you leave a town and you see all of the forests and you get attacked by creatures every 5 seconds?(and no you can not do this in a cave the game does not allow it) so after you leave a town press the character menu (and no not the menu that says items, magic, equip...). any way press the character menu button and the word "SAVE" will not be gray it will be white. so save after every battle (al least thats what i do because i am afraid i will die in the next battle unless my enemies are weak) and when you get up to the stone dragon gaurding the path to the oracle, use only heal spells, heal items, the spell gloom, and melee attacks. anything else does zero damage to it. and make sure that noslom is at level 10 and knows the spell "LIFE" and also have ajathar with you because he is the only one so far on your team by then who can use a hand axe which does like 68 damage to the dragon NORMALLY so make sure that 1. noslom knows life, 2. ajathar is on your team, 3. ajathar has a hand axe, and 4 . that you constantly heal them when their health is near 70 or 68 because the dragon knows a spell called FADE which does like 38 to 63 damge to both noslom and ajathar.

---

### Post by comicman100 on 2009-10-20
> **comicman100 said:**
> ok so you when you leave a town and you see all of the forests and you get attacked by creatures every 5 seconds?(and no you can not do this in a cave the game does not allow it) so after you leave a town press the character menu (and no not the menu that says items, magic, equip...). any way press the character menu button and the word "SAVE" will not be gray it will be white. so save after every battle (al least thats what i do because i am afraid i will die in the next battle unless my enemies are weak) and when you get up to the stone dragon gaurding the path to the oracle, use only heal spells, heal items, the spell gloom, and melee attacks. anything else does zero damage to it. and make sure that noslom is at level 10 and knows the spell "LIFE" and also have ajathar with you because he is the only one so far on your team by then who can use a hand axe which does like 68 damage to the dragon NORMALLY so make sure that 1. noslom knows life, 2. ajathar is on your team, 3. ajathar has a hand axe, and 4 . that you constantly heal them when their health is near 70 or 68 because the dragon knows a spell called FADE which does like 38 to 63 damge to both noslom and ajathar.
was this info helpful to you?

---

### Post by comicman100 on 2009-10-20
hey does anyone know what to do after you go through the teleportation thing in the oracle's cave because every time i am in the town it transports me to i don't know where to go or what to do due to the fact that i just wander around aimlessly trying to find another teammate or just get to the town where people actually welcome me politely. HELP! PLEASE?

---

### Post by comicman100 on 2009-10-25
ok guys so i have a question. i just bought Trezin's house (the one in 
Maldea) so i just baught it and i have no idea what to do now. i mean i have all of the opal stuff and i am stuck. please help me i don't know what to do. PLEASE HELP!:confused::confused::confused::confused::confused::confused:

---

### Post by darling99 on 2009-11-07
> **oki_180sx said:**
> intall "scanmem" via
apt-get install scanmem

open terminal while KQ is running

remember the number it gives you

now


it will scan for that value that you input
so buy something, then search for your amount of gold you have now
once it narrows it down to one result, the type
set "value of gold you want"
**that so does not work!**

---

### Post by darling99 on 2009-11-07
I am at the part in the oracles castle and there are 4 button things on the floor what do I do?? :confused:please help

---

### Post by jakestrictor on 2009-11-07
ok to get past there step on one of the darker tiles, there sould be 4 tiles, 1 first step on the tile  upper right, 2 and you mite have to step on upper left dark tile, if you have any problems tell me, oh btw you go behind the gap in the ground, go around it

---

### Post by spike.robinson on 2009-11-11
As I have not been able to find a Walkthrough anywhere on the web, and this seems to be the right place, I'm going to post a sort of combination Walkthrough and Tutorial here. I'm going to do it in parts, roughly corresponding to the 8 phases of the game. 

Please feel free to offer comments and corrections!

---

### Post by spike.robinson on 2009-11-11
KQ WALKTHROUGH

PART 1 - MANOR, EKLA, TUNNELS, GROTTO

NOSTIK'S MANOR

Talk to Hennert to get money.
Leave.
On World Map, go to the town to the NE
(you can visit Grotto first but not much advantage apart from gaining a free healing herb)

EKLA

Speak to guard (green) for advice and to find out about the problem in Ekla. 

The greeter boy (blue) is largely irrelevant. Perhaps a hint that the other 7 adventurers have already passed this way? (though if so, how did they get out with the tunnel blocked?)

You can go behind the houses east of the Inn. In the yellow flower bed just NE of these houses you can find 155gp. Not essential but very handy at the start of the game. 

Spells can be sold in an unmarked house SE of the Inn. There is a 'free' spell scroll there, Scorch, in the chest which you can just open and take. There is not much point buying anything there as the only spell she has, you already know. Later, with new characters you might want to buy spells here. Maybe. 

Before you can use a spell, you need to read the scroll of that spell, using the Items menu. Then the spell is learned, and appears in your Magic menu. 

Continuing south, you can go to the west to weapons shop (marked with a sword) and armour shop (shield), or east to the potions shop. The potions shop here also sells some spells (Shield). In a pot to the west of the potions shop is some Nerlilam leaf, useful against poison. This will be valuable soon, as you will encounter poisonous monsters.

The initial combination of items you buy with your limited funds is up to you. You will not be able to buy everything you want or need, initially. 

At first, I would recommend not buying Salve - it restores more hit points than your maximum. Nor the Shield spell - a real shield is more use at first. Everything else on sale is pretty useful, and the costs are well balanced against the advantages. 

Suggested equipment

You only need 1 weapon, preferably one handed so that you can later use a Shield as well. You probably don't need more than one cure item, for emergencies, since you can Cure yourself with a spell. One or more anti-poison items is useful, though you can find a free one (see above). If you plan to use magic offensively (Scorch), you might want an extra cure item or two. The bulk of your money should be spent on the best total armour you can afford. 

For 200gp you can buy a Robe and Rapier, this is a good start. If you have more money, buy more armour: Shield, Gloves, Cap (in that order). You could buy Leather Armour instead of a Robe, if you have an extra 75gp, but it's only a little extra defence and you lose some evasion and a lot of magic defence. It will be a while before you face magic using monsters but when you do, the magic defence will be critical. 

With 407 gp (finding the gold pile and selling initial arms) I would buy: Rapier, Robe, Shield, Gloves, Cap. Don't buy any cures, just carry the 2 free ones you've found (see above). This costs 390gp, leaving you 17gp. With reasonable luck you will find another 8gp before you need to recuperate in the Inn. 


In general you buy/sell things by facing the shopkeeper, right in front of them, and pressing the action key (space). For weapons and armour, the display will show the relative improvement/impairment of switching to that item, vs your current equipment.

Before you go into the armour and weapons shops you should un-equip your starting arms (Knife and Garment) so that you can sell them (40gp and 12gp). Items cannot be sold while they are still Equipped. If you plan to sell your starting items, sell them first, so you know how much total money you have available to spend. 

After you buy weapons and armour, you need to use the Equip screens to place them.  This screen can also so you the relative effects of different weapons, armour, etc, if you want to fine tune them. It's ok just to use the Optimise option initially, letting the game place them as it thinks best.

Remember to sell any surplus items you get later, as you upgrade, as this will generate a bit more cash. 

In the extreme SE of the town is a house in a walled garden. This is Derig's house. Talk to the woman in there. She sends you back to the Grotto to find Derig, who will provide more information. 

You can find Derig at any time. See 'GROTTO'

Art Shop

Just northeast of the armour shop is an art shop. I have not figured out what if anything can be done in here. There is a suit of mirror-polished armour but it does not seem to be for sale. There is a child, an art collector, and a shop keeper. She was hiding the art from Malarkon's forces. There is a locked cabinet. 

Lower guard (green). Near the tunnel entrance, a walled off square at the bottom of the map, is another guard. He tells you that a monster is blocking the tunnel to Randen. This is your quest in Ekla - to eliminate the monsters and unblock the tunnel. 

Tactics for Ekla Tunnel

As the guard suggests, you will need to train up, gain experience and gold, before you can defeat all the monsters who control the Tunnel. You should make cautious forays into the Tunnel, or into the surrounding country, fight monsters, then return with gold to buy more equipment/spells. Be cautious at first. 

You exit the town at the NW, where you came in, by the Inn. 

After each foray, you will need to go the Inn to rest, to recover your Magic Points (and also hit points). This costs 25gp, so it's a good idea never to let your gold fall below that level. You may have to run away from a fight and come back empty handed. 

Ultimately, even killing all the monsters in the tunnel won't solve the problem, as they are spawning. You need to prevent them from spawning. See GROTTO. 

GROTTO

The grotto is in the clearing in the center of the forest, directly north and slightly west of Ekla. Go as quickly as you can to reduce the risk of encountering wandering monsters. 

Fall down the hole by walking on the flowers. In the hole, get the healing herbs from one of the pots on the right if have not already done so. You can check the opening to the north, but it is blocked by a strange barrier. This makes the portal-type light appear. If you touch this, Derig will notice you and take you back to the surface.

Talk to Derig.  He will transport you back to his house in Ekla town (no monsters on the way). 

Derig explains you need to get a Unadium coin from his daughter, go back to the grotto, open the rune there with the coin, retrieve a Rod of Cancellation, and use it to close a portal in the Tunnel. Only then will the Tunnel be safe. 

NB you will need to be stronger to complete these missions, build up your experience and equipment before attempting to finally complete them. 

Talk to Derig's daughter to get the Unadium coin. 

Now you can do some practice forays into the Tunnel, or into the wilderness, before you go and retrieve the Rod of Cancellation. If you go to the wilderness, don't stray too far from the town. Otherwise if you are badly hurt you might not make it back to town and the Inn. 

Remember, each foray must bring in at least another 25gp so you can recover at the Inn. Always hold on to at least this much, maybe twice (50gp) once you can afford it. 



TUNNELS

You will be accosted by monsters in these tunnels. Watch your health. Use cure spells. When your magic is running low, get out - live to fight another day. You can gain valuable gold and experience. 

Goblins you can handle with a Rapier. Giant spiders, take no chances, use Scorch on them. If you meet 2 giant spiders, consider running, unless you totally get the jump on them. If they damage and/or poison you before you get to attack them, definitely run. (Attack option, then right arrow brings up Run). Scorch will defeat any of the initial monsters reliably, but is particularly effective on Skeletons.

Generally use Cure to cure yourself rather than Items, except in emergencies. Since a curing herb costs as much as a night in the Inn, only use it to save your life, and then get out of there. 

If you get a venomous bite, you need to treat it with an Item asap. Don't bother curing hit points until you stop the venom, otherwise you will just lose more hit points again. The venom makes you lose hit points every round. Be very careful. In most cases it makes sense to run away once poisoned, unless you are absolutely sure you can finish the fight before you die from poison. (Actually I'm not sure if I've got the poison mechanics correct.)

The East branch of the tunnel leads to Randen, but is blocked. A dying guard warns you not to continue. You should not go that way until you know how to solve the problem. You will also need to be strong to defeat the monster guarding (a Dark Imp). Probably you want to be 3rd Level, or 2nd level and very lucky/careful, before you can defeat a Dark Imp solo. 

South there is some treasure you can collect. 
The southeast fork leads to a chamber with pots. There is a healing herb in one of the pots (lower right area).

There is also a false wall on the west side of the entrance to the chamber. 

Push the action button to open the secret door. This teleports you to a chamber containing chests. (The chamber is visible in the NW of the tunnels, but not reachable) There is a Rune of Water, and some steps down. However the steps are blocked. You can return to the tunnels by going back to the portal. 

**When to the steps get unblocked? Not when the portal is closed, not when Ajathar joins, not when the bridge monsters are slain...**

In the SW is a chamber containing a Portal. This is how the monsters are coming through, and it is what you must deactivate to complete the Ekla quest. See GROTTO.

ROD OF CANCELLATION 

You can probably do this even at Level 1
From the grotto you teleport to a forest
Follow the left wall. There are monsters but mostly easier ones such as goblins, centipedes, and (wimpy, low damage, non poisonous) grass spiders. Early on there is a chest with a Leather Helm which will improve your defence slightly. The Rod of Cancellation is in the second chest you find. There is no need to fight too many bad guys, or explore the rest of the forest (unless you want to).


After completing this, go back to Derig. He takes the Rod and Unadium Coin. If you talk to his daughter, she will give you a SunStone. This can only be used in daylight, and not in combat, but it will (once) restore all HPs and MPs for all your party. You probably want to save it until you are much higher level and in a very difficult situation.

The Dark Imp is still there however! You probably need to be L4 to defeat the Dark Imp solo. He will take at least 2 Scorch hits to kill, so even if you are lucky and surprise him, or get the first shot in the second round of fighting, you need to be able to absorb 1 Scorch hit. More likely 2 hits. You definitely want to be wearing the Wizard's Robe (for extra Magic Defence) if you weren't already. If you are really lucky, the Dark Imp will do a melee attack instead of Scorch or Venom. But you're not lucky, you will die!

Once the Dark Imp is dead you can get through to Randen.

---

### Post by spike.robinson on 2009-11-11
PART 2 - RANDEN, ORC CAMP, BRANDYN RIVER


RANDEN

Once in Randen you immediately meet up with Ajathar. He was guarding the tunnel at the Randen end. Now the tunnel threat is ended, he offers to join up with. You sure could have used his help fighting that Dark Imp!

The first thing you want to do in Randen is trade up to the better armour, weapons and spells available here. If you don't have gold, go and get some!

heading East from the town entrance:

Woman in first house knows there are adventurers around

Second house is empty

Mayor's house - guard reports worried that Mayor is away in Andra and he ought to be back by now. 

Third house. Woman downstairs has a Phoenix Blade. **Need something to trade with her for it? She doesn't seem to take the Long Knife or regular Knife. But how do you trade, anyway?**
From the drawers in her middle room you can "Procure" Larinom Tonic, which will raise someone from the dead - useful!
Go up 2 flights of stairs from her far room, to the upper attic, and there are 3 chests. You can procure some Salve, 250gp, and a Long Knife. The Long Knife is a good weapon, far superior to the Rapier, and with none of the penalties to Aura. As the Rapier is inferior to Ajathar's weapon, the Morningstar, the Rapier is now obsolete and can be sold.

Just down from this house is the weapons shop, also selling armour. Ideally you want to upgrade Nolsom to a Wizard's Robe (750gp) and then a Quartz Band (250gp), both of which Ajathar already has - that will set you back a grand. Then you want to upgrade first Nolsom, then Ajathar, to a Half Spear - a further 700gp each. Time to go make some more money! If you don't have the money for the Wizard's Robe, don't buy any other arms, save up until you can afford the Robe - it is much more useful than anything else. 

There are also nice new spells available here. Sleep and Silence. Sleep is ok for taking a powerful opponent out of the action for a few rounds while you focus on the others - if you can get it to work. For most opponents at this level, it's easier just to kill them with Scorch, rather than messing about with Sleep. But Silence is invaluable when dealing with magic-using monsters. Both characters should get Silence asap. Ajathar is 1st level now but he will be 2nd level in the blink of an eye so it's worth buying the spells as soon as you can. Realisticaly you probably won't have the money until Ajathar is 2nd level or higher. I would probably recommend the silence spell even above any of the weapon/armour purchases. If you have around 500gp, maybe buy 2 Silence spells - one each. But you will have to come back later for the second one, as they only carry one in stock. 

(You also might want to go back to Ekla to buy Ajathar a Shield spell, at some point.)

Various characters in this town tell the story that the bridge is out and it needs to be repaired. That's your main quest for Randen. They also wonder about the fate of the mayor, which is the side quest. 

In the house on the left, above the Inn, is an old woman whose husband is late. The mayor's wife perhaps?

The town exit is to the south (not the Ekla tunnel where you came in, which is in the NW corner).

Before you go to the river, you need to level up. Try the Orc Camp for starters. Be careful with Ajathar.

ORC CAMP

This is located in the small wood in the south center of this map, so SE from Randen. You will encounter higher level orcs, some using magic wands. There can be as many as four of them. Don't be afraid to run if the odds are against you or if things go badly. 

If you follow the right wall (from your characters' perspective), after tackling 3 groups of orcs you will come to a single guard. You may need to press the action key to fight some of these groups, but others will attack on sight. Behind the single guard is a stash of treasure - bronze armour and a Half Spear, very valuable arms at this point. The Half Spear is an improvement over the Morningstar but arguably not any clear advantage over the Long Knife, so probably give it to Ajathar. The Bronze Armour, compared to the Wizard's Robe, gives a defence boost, but an equal penalty to magic defence, plus a penalty to evade. Compared to the Cloth Robe, it's not so bad. If you have not yet upgraded armour, it might be worth swapping so that Noslom has the Wizard Robe, Ajathar gets the Bronze Armour. But keep in mind Ajathar will be more vulnerable to magic this way, and there is a fair amount of magic being used against you now. "Optimise" will replace the Wizard Robe with the Bronze Armour, but I'm personally not so convinced...

Anyway after getting this treasure is probably a good point to go back to town for a rest, and maybe spend some of that money you've got - possibly on a second Wizard Robe. 

The second part of the Orc camp continues from just east of this point, where there is a narrow gap in the trees that you can't walk through. This is often reported as a bug. In fact, there is an "invisible" guard standing south of this gap, blocking your way. You need to face this invisible guard, press the action key (space) to start a fight with him.

After this you head roughly north through about 3 groups of orcs until you find a group of orcs guarding a cage with human civilians and guards in it. You have to get through 4 Zemmel Orcs wielding magic wands. This is tough but doable. 

You have a conversation with Cassandra and the Mayor, who then say they will meet you back at Randen. 

You continue on the last leg of clearing out the Orc Camp. This is a sort of maze of single Zemmel Orc guards, which are much easier to deal with than groups. You should be able to do it without using magic, which is just as well as you may be a bit low on magic at this stage. 

They are guarding a number of treasure chests including Elimas drops (restore lots of MPs), Salve x2, Rune of Recovery, 250gp, Nerilam Leaf x2, etc.

In doing this maze you need to be systematic or you will miss things, e.g. follow the left wall or the right wall. But, be careful not to exit prematurely near the SE corner of the map. This south exit is near a patch of mud, above a 2-tile-wide north-south path in the wood.

Otherwise you will have to fight your way through the whole camp again to get the remain treasures. Of course, you might want to to just that, to get experience...

In the maze are a few lost guards who you can talk to. One implies he'll do you a favour later...



Once back at Randen, you get praise from the townsfolk. Cassandra is waiting at the first cross roads. She explains a bit more about the Mayor and why he was going to Andra. She can join your party at this point, but since she is 1st level, and you and Ajarath are probably 4th-5th level or better, you will probably decline. 

At some point the Orc Camp disappears. **What triggers this? Mission completion does - something earlier? What if you leave, say, one Orc alive - do they all regenerate? Does this allow "Camp Milking"?**

You will have a lot of cash from the Orc Camp, so you can gear up in the armour shop and maybe buy some potions or even spells. You might now be ready to tackle the problem at the Bridge. If not, you can go back into the wilderness for some more fighting experience. 

At the end of the day I think the Wizard's Robe is better than the Bronze Armour or the Fighting Suit. All offer a fair balance of magic defence vs physical defence. However I think that hit points are easy to gain and easy to recover, even during combat. Magical effects during combat are usually much more debilitating,and much more expensive to fix, than losing even 20 points more of HP during the course of a combat. And they are more likely to get you dead. So I will favour the Wizard's Robe. I will hang on to the Bronze Armour, but only use if it I know I'm going in to a non magic using situation (actually the River Slimes would be a good example of that, their attack is physical). 

Even then you need to look at the lower Evade effects... so maybe the Fighting Suit is a better choice, as it has no Evade penalty relative to the Wizard Cape. Still, it's expensive at 800gp a pop, for a marginal benefit (+2 defence) for just for one battle. I guess you could "rent" the suits for 400gp each, i.e. sell them back afterwards... nah, not worth it. Maybe Evade doesn't apply to the Slimes' Flash Flood attack anyway. For that matter, maybe physical defence doesn't resist it either. 








BRANDYN RIVER

If you talk to the workmen and guards, and then leave, they shout for help and they are being attacked. It's hard to spot but there is a group of creatures in the water. Click the action button on it to initiate combat. 

NB you probably need to level up before facing this. You need to dish out 160HPs to kill the 2 river slimes And you need to be able to soak up as much as 40 to 80 HP per round on each character while doing so. That probably means high hit points, AND someone using strong potions (Salve or Cure2) every round. You probably need both characters around 6th level before you can beat these guys. You will also need to buy the best armour and weapons available in Randen first. So hang out and do some adventuring before going to the bridge. Maybe go looking for the mayor first? In particular, since Ajathar is only first level, you need to train him up carefully first - maybe travelling back to Ekla's surroundings. 


It seems the powerful Flash Flood attack is magical, so Wizard Robes and high Magic Defence is preferable to high armour. 

An option is for Ajarath to do holds on them while Nolsom does Scorch. Ajarath can do more damage that that with his half spear, but having the Slimes attack you while you are trying to kill them is too dangerous. Conversely, Silence might work to prevent the Flash Flood attacks - not clear.

I tried Sleeping, Holding and Silencing them. Hold and Silence did work. Silence did seem to stop the Flash Flood attacks, but it's hard to tell since it only works a few turns anyway. And there is no way for us to tell (as magic using monsters seem to tell) when the spell is about to wear off. 


I think the best tactic is probably the old fashioned one - offense is the best defence, concentrate your firepower. So do a double attack on round 1 against one slime to kill it and reduce the number of opponents to a more manageable number. From then on, one character (probably Nolsum because his cures are cheaper and he has more MPs) cures the damage caused by the first and the remaining slime, while the other character (probably Ajathar since his attack does more damage) attacks the slime. 

After killing the Slimes, the workmen tell you the bridge will be built soon, come back soon. So you head back to Randen

---

### Post by comicman100 on 2009-11-24
> **NHmomma said:**
> Hi,

I was going to start a new thread, but maybe if I post as part of this one, someone could help.

I recently downloaded this one, and have attempted to play a bunch of times, but for some reason, I cannot seem to save my game.  The menue comes up with save grayed out.  I thought maybe if I just got farther then I could save, but I have made it all the way to getting a second adventurer with me in the second city, and still no save option...  Getting tired of having to keep hitting the space bar through the beginning stuff...

Any suggestions?

Ok so here is the thing you can only save when you are on the travel map, on a circle on the ground with an "S" on it, or when there is a hole looking thing on the floor that you can walk over and there is a yellow light coming out of it. then you press the button for the character menu which is "Esc" and it will have the words "save, load, conf. which means configure, and exit"

---

### Post by spike.robinson on 2009-11-30
Delay in writing up part 3 of the walkthroughs for Andra, Temple, Denorian Village, and Oracle. The reason is that the troll side quest for Denorian Village seems to be incomplete, at least in the most recent stable version. Possibly it is complete in the CVS version, but in the version I have (kq-linuxbin-20080202 from the Sourceforge repository), when you find the troll level boss you just get a message saying "Not Yet Implemented" or something along those lines. 

I may do the write ups anyway if I get some spare time.

---

### Post by Markgov on 2009-11-30
I've just arrived to a point were i can't do anything else. I've collected 3 of 4 pieces of the Opal Set and i need only the armor but after i collect the third piece after saving the little girl kidnapped, i receive a Cave Key from the father; he say to me: <the key unlook the doors in the mountain pass, i've remembered something about the Opal Armor, there is a magical suite of opal armor locked away deep in the mountain, the key will unlock the sealed entrance to the dungeons below, a dark race of Larinon live in the dungeons.>.
But which MOUNTAIN PASS and CAVE is he talking about?? 
There is a closed cave near the town where of Pulcannen that u reach using the travelpoint inside the Oracle Cave the second time u use it but that cave say <this is where a new cave goes>. 
Maybe it's an uncomplete point? or i have to find something else? 
thats what u get playng uncomlete games i think... 

(the game is good but the developpers need to improove the dialogue because too many time u dont now where u have to go next a u just go around everywhere tryng to find somthing becoming crazy!!!)

---

### Post by MrNiceGuy95 on 2009-11-30
At first, I realy like this game.
But there are some bugs who degrades the game fun.
I downloaded the game from the software center and there was a bug at dungars house, but i fixed it. And now, I have the next problem.
I have every part of the Opal armor, got the house and now i dont know what to do next.... 
I went inside the tower where i was able to go in if i got the 4 parts.
but there was nothing else... there were some villages but there was nothing interesting. and there were two caves i werent able to get in and two towns i werent too.
could it be that i have an too old version and the game is not finished there? i think its the 2007 version... i installed a package for continue at dungars house but now i dont know what to do... thanks for help ;):KS

---

### Post by MrNiceGuy95 on 2009-12-01
Damn! next problem. i got the rusty key and i dont know what grotto he means.... there is a grotto in the forest but i cant go there....

---

### Post by comicman100 on 2009-12-02
> **MrNiceGuy95 said:**
> Damn! next problem. i got the rusty key and i dont know what grotto he means.... there is a grotto in the forest but i cant go there....


if you returned the unadium coin and the rod of cancellation to Derig then you are screwed because it is talking about the grotto where you found Derig and you need the unadium coin to get to the temple. it is the temple that is near the rod of cancellation.

---

### Post by MrNiceGuy95 on 2009-12-03
ah okay and where i get the unadium coin? i talked to derig's granddaughter but she just says thanks again... and i cant talk to derik

---

### Post by linux9978 on 2009-12-20
actually if you progress further to the temple,a save option is present, i found this afer several level 9 characters died terrible deaths, and once was fighting a random lvl 23 group
lol i died after a doube fire wall attack:guitar:

---

### Post by linux9978 on 2009-12-20
> **comicman100 said:**
> hey does anyone know what to do after you go through the teleportation thing in the oracle's cave because every time i am in the town it transports me to i don't know where to go or what to do due to the fact that i just wander around aimlessly trying to find another teammate or just get to the town where people actually welcome me politely. HELP! PLEASE?
yeah actually go down to surinan or anjanthar and tward the bottom of those towns(the former i think)   youll see a travel point, which will send you to randell next to the mayors establishment and from there just head back to nostiks

---

### Post by thomasrodinel on 2010-01-10
ei how can i fix the dungar house bug???

after dungar dies i seem stuck and the program automatically closes.... help anyone.

---

### Post by thomasrodinel on 2010-01-12
for the dungar house problem.... you need to download an estate.lua... i forgot where i found it...

i now have the 3 opal set except the opal armor...

after i saved a girl i now have a key which allows one to pass a cave located in the caravan pass/ mountain pass. you have to buy dynamited to pass though boulders/rocks...

when i reach deeper in the caves... KQ crashes??? have somebody experienced this??? what am i going to do???

where can i find the opal armor set to be able to complete them?? help please...

---

### Post by thomasrodinel on 2010-01-12
ey mr nice guy... i already have the 3 opal equipment except the armor...

when i went to the caravan pass/ mountain pass and inside the cave...
i have to set dynamites for i to go pass through the cave right???

but when i reach the farthest part of the cave... the game crashes???
did you also experienced it??? what did you do??

where did you obtain the opal armor???

thanks!!! hope you'll reply ASAP.

---

### Post by gwionn on 2010-07-08
I've found you can simply edit the save file, works with all my other games

---

### Post by Gene393 on 2010-07-23
Hi, I got it recently and the daughter in the first town tels me to go see derik in the grotto north, here is this? also I cant acsess the quests menu

---

### Post by vipinpv85 on 2010-07-26
Always when I enter the arena I get message "I am not ready yet!". what to do?

Hi All, finally I got through that level (Actually the characters say "I am not ready yet"; But you can go back & talk to person whom you registered he will redirect you to next match)

Anyone knows where to find opal armor?

> **William5 said:**
> you are permitted to save game only u stand on the save point~

Well I am able to save (outside towns & caves); using alt+esc it pops up menu for "save, load, exit" options.

how to open the opal caves (opal armour is there somewhere?)
How to open the doors at the mines?

Key to mountain caves ==> got to Ajantara, meet parents of the Girl rescued. they will hand over the key.

Come back to mountain caves; defeat spirits & bug monster.

What to do next. How to open Opal caves?

---

### Post by vipinpv85 on 2010-08-09
> **vipinpv85 said:**
> Always when I enter the arena I get message "I am not ready yet!". what to do?

Hi All, finally I got through that level (Actually the characters say "I am not ready yet"; But you can go back & talk to person whom you registered he will redirect you to next match)

Anyone knows where to find opal armor?
>> its inside caves, once defeating the dragon search the jewels lying in that area

Well I am able to save (outside towns & caves); using alt+esc it pops up menu for "save, load, exit" options.

how to open the opal caves (opal armour is there somewhere?)
How to open the doors at the mines?
>> we will get the mine door keys form the girls father; whom we rescued.
Key to mountain caves ==> got to Ajantara, meet parents of the Girl rescued. they will hand over the key.

Come back to mountain caves; defeat spirits & bug monster.

What to do next. How to open Opal caves?
>> I reached back to pullikan after acquiring all the armour stuff, there i was given a key to go to grotto; when inserted key; it says not implemented.

>> went to through the caves ot the tower, there also things seems to be incomplete

---

### Post by MagnusDicander on 2010-08-17
I have just upgraded from ubuntu 9.04 to ubuntu 10.04. After this upgrade, KQ will not allow me to play with sound. The sound works in every other application, but not in KQ.

---

### Post by vipinpv85 on 2010-08-17
> **MagnusDicander said:**
> I have just upgraded from ubuntu 9.04 to ubuntu 10.04. After this upgrade, KQ will not allow me to play with sound. The sound works in every other application, but not in KQ.

>> while using ubuntu (pulse volume) same issue exiist

---

### Post by CPL2010 on 2010-08-17
gamefaqs.com

I've been using it for at least 7 years to find my walkthroughs and cheats.

> **thrasher6900 said:**
> So I'm playing this KQ final fantasy like game.

But I'll admit, I like to cheat a little(money mainly) to get a leg up and move things along faster.

I was wondering if anybody had any information on this game.


I tried googeling it and it just comes up with "Kings Quest" and every potential link isn't valid and takes you to spam :|

I'll appreciate your input. . . ....unless of course you decide to be all moral and post stupid comments like "just play it normally blah blah blah you suck for cheating blah"

---

### Post by CPL2010 on 2010-08-17
And the ALSA mixer is setup as the sound under wine?  For Kings Quest it's kind of old and runs easily under a VM with WinXP.  The older DOS/Win games I have no problem running under SUN Virtual box with a nLited XP guest (rip out everything non essential until the OS footprint is under 200 megs, compile the ISO then install from the ISO.  XP runs like a porche on crack)

Even a handful of FPS run under it with 3d emulation, it is limited to running like a POS Intel 915GM video card though, so frame buffer/shading...well anything over a quake 2 engine stinks on it.  Depends on your specs really.  I'm on a Dell Latitude 9400 with the X1400 Radeon and 256 meg on the video card.  It even runs wow at around 25-30 fps.  Not fantastic, but it's functional.

> **vipinpv85 said:**
> >> while using ubuntu (pulse volume) same issue exiist

---

### Post by Above on 2010-09-10
> **MagnusDicander said:**
> I have just upgraded from ubuntu 9.04 to ubuntu 10.04. After this upgrade, KQ will not allow me to play with sound. The sound works in every other application, but not in KQ.


I had the same problem until I found a post online stating that pulseaudio has some sort of conflict with the game and needs to be removed to allow ALSA to work properly. So if you follow the steps outlined [here,]("http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8284273&postcount=4") on how to remove pulseaudio to the letter, once you load KQ you will now have the option of turning the system sound On.
Hope this works for you!

---

### Post by Above on 2010-09-10
> **thomasrodinel said:**
> ei how can i fix the dungar house bug???

after dungar dies i seem stuck and the program automatically closes.... help anyone.

Here are the steps you need to follow at this website:

[http://us.generation-nt.com/answer/bug-537798-kq-bug-at-dungar-estate-help-168963471.html](http://us.generation-nt.com/answer/bug-537798-kq-bug-at-dungar-estate-help-168963471.html)

I am using ubuntu 10.04 and these steps fixed the glitch in the game. Just make sure to spell and space everything correctly. It took me 6 tries but it solved the Dungar house bug.

---

### Post by erikthedrink on 2010-09-30
Hi.  I know this advice comes late.  If you know how to do 'pidof kq' and scanmem 'pidof kq', then here is the list for the item codes from the opensource file.  With these codes, you can modify your items early in the game.  You can get the opal items early!  Yes, there are the unagi items.  Unagi items are more powerful than the opal, yet the opal items are part of the quest.

```

#define I_MACE1             1    /* Mace */ 
#define I_MACE2             2    /* Morningstar */ 
#define I_MACE3             3    /* Frozen Star */
 #define I_MACE4             4    /* Death's Head */ 
#define I_HAMMER1           5    /* War Hammer */
 #define I_HAMMER2           6    /* Stun Hammer */
 #define I_HAMMER3           7    /* Battle Hammer */
 #define I_HAMMER4           8    /* Thor's Hammer */ 
#define I_SWORD1            9    /* Rapier */
 #define I_SWORD2            10   /* Short Sword */ 
#define I_SWORD3            11   /* Long Sword */
 #define I_SWORD4            12   /* Katana */ 
#define I_SWORD5            13   /* Great Sword */ 
#define I_SWORD6            14   /* Dragon Sword */
 #define I_SWORD7            15   /* Avenger Blade */ 
#define I_AXE1              16   /* Hand Axe */ 
#define I_AXE2              17   /* Battle Axe */
 #define I_AXE3              18   /* Hunter's Axe */
 #define I_AXE4              19   /* Slayer's Axe */ 
#define I_KNIFE1            20   /* Knife */
 #define I_KNIFE2            21   /* Long Knife */
 #define I_KNIFE3            22   /* Balmar's Dagger */ 
#define I_KNIFE4            23   /* Aichasi Knife */
 #define I_SPEAR1            24   /* Half Spear */
 #define I_SPEAR2            25   /* Long Spear */ 
#define I_SPEAR3            26   /* Battle Spear */
 #define I_SPEAR4            27   /* Chaku Spear */ 
#define I_ROD1              28   /* Iron Rod */
 #define I_ROD2              29   /* Rod of Fire */ 
#define I_ROD3              30   /* Gloom Rod */
 #define I_ROD4              31   /* Crystal Rod */ 
#define I_ROD5              32   /* Temmet Rod */
 #define I_STAFF1            33   /* Staff */
 #define I_STAFF2            34   /* Soul Staff */ 
#define I_STAFF3            35   /* Defender Staff */
 #define I_STAFF4            36   /* Pentha Staff */
 #define I_STAFF5            37   /* Maham Staff */
 #define I_SHIELD1           38   /* Wooden Shield */ 
#define I_SHIELD2           39   /* Iron Shield */
 #define I_SHIELD3           40   /* Steel Shield */
 #define I_SHIELD4           41   /* Tegal Buckler */
 #define I_SHIELD5           42   /* Aegis Shield */ 
#define I_SHIELD6           43   /* Opal Shield */
 #define I_SHIELD7           44   /* Unadium Shield */
 #define I_CAP1              45   /* Cap */ 
#define I_CAP2              46   /* Wizard Cap */ 
#define I_CAP3              47   /* Bandanna */
 #define I_CAP4              48   /* Ribbon of Ayol */
 #define I_CAP5              49   /* Mask of Tyras */
 #define I_HELM1             50   /* Leather Helm */
 #define I_HELM2             51   /* Iron Helm */ 
#define I_HELM3             52   /* Steel Helm */ 
#define I_HELM4             53   /* Opal Helm */ 
#define I_HELM5             54   /* Unadium Helm */
 #define I_ROBE1             55   /* Cloth Robe */ 
#define I_ROBE2             56   /* Wizard's Robe */
 #define I_ROBE3             57   /* Sorceror Robe */ 
#define I_ROBE4             58   /* Arch-Magi Robe */
 #define I_ROBE5             59   /* Trenta Robes */ 
#define I_SUIT1             60   /* Garment */
 #define I_SUIT2             61   /* Fighting Suit */ 
#define I_SUIT3             62   /* Battle Suit */ 
#define I_SUIT4             63   /* Flanel Shirt */ 
#define I_SUIT5             64   /* Power Suit */ f
#define I_ARMOR1            65   /* Leather Armor */ 
#define I_ARMOR2            66   /* Bronze Armor */
 #define I_ARMOR3            67   /* Chain Mail */ 
#define I_ARMOR4            68   /* Gold Armor */
 #define I_ARMOR5            69   /* Plate Mail */ 
#define I_ARMOR6            70   /* Dragon Armor */ 
#define I_ARMOR7            71   /* Opal Armor */
 #define I_ARMOR8            72   /* Crystal Armor */
 #define I_ARMOR9            73   /* Unadium Armor */
 #define I_BAND1             74   /* Quartz Band */
 #define I_BAND2             75   /* Adamant Band */
 #define I_BAND3             76   /* Opal Band */
 #define I_BAND4             77   /* Unadium Band */
 #define I_GLOVES1           78   /* Gloves */
 #define I_GLOVES2           79   /* Ninja Gloves */
 #define I_GAUNTLET1         80   /* Battle Gauntlets */
 #define I_GAUNTLET2         81   /* Titan Gaunlets */
 #define I_GAUNTLET3         82   /* Force Gauntlets */
 #define I_SPEEDBOOTS        83   /* Boots of Speed */
 #define I_HERMES            84   /* Hermes Shoes */ 
#define I_AGRAN             85   /* Agran Talisman */
 #define I_EAGLEEYES         86   /* Eagle Eyes */ 
#define I_PURITYGEM         87   /* Gem of Purity */
 #define I_MANALOCKET        88   /* Mana Locket */
 #define I_MESRA             89   /* Mesra Feather */
 #define I_OCEANPEARL        90   /* Ocean Pearl */
 #define I_POWERBRACE        91   /* Power Brace */
 #define I_PRIESTESS         92   /* Priestess Charm */
 #define I_REGENERATOR       93   /* Regenerator */
 #define I_RUBYBROOCH        94   /* Ruby Brooch */
 #define I_SHADECLOAK        95   /* Cloak of Shades */
 #define I_DEFCLOAK          96   /* Defense Cloak */
 #define I_RUNECLOAK         97   /* Rune Cloak */
 #define I_SPIRITCAPE        98   /* Spirit Cape */
 #define I_WOODCLOAK         99   /* Woodland Cloak */
 #define I_WATERRING         100  /* Water Ring */
 #define I_PALADINRING       101  /* Paladin's Ring */ 
#define I_RILOCRING         102  /* Riloc's Ring */
 #define I_MHERB             103  /* Medicinal Herb */
 #define I_NLEAF             104  /* Neliram Leaf */
 #define I_OSEED             105  /* Olginar Seed */
 #define I_STRSEED           106  /* Selingas Seed */
 #define I_AGISEED           107  /* Amasian Seed */
 #define I_VITSEED           108  /* Vecindu Seed */
 #define I_INTSEED           109  /* Ingral Seed */
 #define I_WISSEED           110  /* Walsiras Seed */
 #define I_EDROPS            111  /* Elimas Drops */
 #define I_EDAENRA           112  /* Elixir of Daenra */
 #define I_KBREW             113  /* Krendar's Brew */ 
#define I_LTONIC            114  /* Larinon Tonic */ 
#define I_NPOULTICE         115  /* Nidana Poultice */
 #define I_PCURING           116  /* Potion of Curing */
 #define I_SALVE             117  /* Salve */
 #define I_WENSAI            118  /* Water of Ensai */
 #define I_HPUP              119  /* Elixir of Health */
 #define I_MPUP              120  /* Mystic Elixir */
 #define I_SSTONE            121  /* Sun Stone */
 #define I_RRUNE             122  /* Rune of Recovery */
 #define I_WRUNE             123  /* Rune of Air */
 #define I_ERUNE             124  /* Rune of Earth */
 #define I_FRUNE             125  /* Rune of Fire */
 #define I_IRUNE             126  /* Rune of Water */
 #define I_TP100S            127  /* TP100S */
 #define I_B_CURE1           128  /* Spell Scroll: Cure1 */
 #define I_B_HOLD            129  /* Spell Scroll: Hold */
 #define I_B_SHIELD          130  /* Spell Scroll: Shield */
 #define I_B_SILENCE         131  /* Spell Scroll: Silence */
 #define I_B_SLEEP           132  /* Spell Scroll: Sleep */
 #define I_B_BLESS           133  /* Spell Scroll: Bless */
 #define I_B_VISION          134  /* Spell Scroll: Vision */
 #define I_B_CURE2           135  /* Spell Scroll: Cure2 */
 #define I_B_HOLYMIGHT       136  /* Spell Scroll: Holy Might */
 #define I_B_RESTORE         137  /* Spell Scroll: Restore */ 
#define I_B_FADE            138  /* Spell Scroll: Fade */
 #define I_B_HASTEN          139  /* Spell Scroll: Hasten */
 #define I_B_LIFE            140  /* Spell Scroll: Life */
 #define I_B_SHELL           141  /* Spell Scroll: Shell */
 #define I_B_WHIRLWIND       142  /* Spell Scroll: Whirlwind */ 
#define I_B_FLOOD           143  /* Spell Scroll: Flood */ 
#define I_B_RECOVERY        144  /* Spell Scroll: Recovery */
 #define I_B_SHIELDALL       145  /* Spell Scroll: Shield All */
 #define I_B_SLEEPALL        146  /* Spell Scroll: Sleep All */
 #define I_B_CURE3           147  /* Spell Scroll: Cure3 */ 
#define I_B_REGENERATE      148  /* Spell Scroll: Regenerate */
 #define I_B_REPULSE         149  /* Spell Scroll: Repulse */
 #define I_B_THROUGH         150  /* Spell Scroll: Through */
 #define I_B_QUICKEN         151  /* Spell Scroll: Quicken */
 #define I_B_TRUEAIM         152  /* Spell Scroll: True Aim */
 #define I_B_WALL            153  /* Spell Scroll: Wall */
 #define I_B_DIVINEGUARD     154  /* Spell Scroll: Divine Guard */
 #define I_B_TORNADO         155  /* Spell Scroll: Tornado */
 #define I_B_FULLLIFE        156  /* Spell Scroll: Full Life */
 #define I_B_CURE4           157  /* Spell Scroll: Cure4 */
 #define I_B_LUMINE          158  /* Spell Scroll: Lumine */
 #define I_B_TSUNAMI         159  /* Spell Scroll: Tsunami */
 #define I_B_VENOM           160  /* Spell Scroll: Venom */
 #define I_B_SCORCH          161  /* Spell Scroll: Scorch */
 #define I_B_BLIND           162  /* Spell Scroll: Blind */
 #define I_B_CONFUSE         163  /* Spell Scroll: Confuse */
 #define I_B_SHOCK           164  /* Spell Scroll: Shock */
 #define I_B_GLOOM           165  /* Spell Scroll: Gloom */
 #define I_B_NAUSEA          166  /* Spell Scroll: Nausea */
 #define I_B_FROST           167  /* Spell Scroll: Frost */
 #define I_B_SLOW            168  /* Spell Scroll: Slow */
 #define I_B_DRAIN           169  /* Spell Scroll: Drain */
 #define I_B_FIREBLAST       170  /* Spell Scroll: Fire Blast */
 #define I_B_WARP            171  /* Spell Scroll: Warp */
 #define I_B_STONE           172  /* Spell Scroll: Stone */
 #define I_B_LIGHTNING       173  /* Spell Scroll: Lightning */
 #define I_B_VIRUS           174  /* Spell Scroll: Virus */
 #define I_B_TREMOR          175  /* Spell Scroll: Tremor */
 #define I_B_ABSORB          176  /* Spell Scroll: Absorb */ 
#define I_B_DIFFUSE         177  /* Spell Scroll: Diffuse */
 #define I_B_DOOM            178  /* Spell Scroll: Doom */
 #define I_B_MALISON         179  /* Spell Scroll: Malison */
 #define I_B_FLAMEWALL       180  /* Spell Scroll: Flame Wall */
 #define I_B_BLIZZARD        181  /* Spell Scroll: Blizzard */
 #define I_B_DEATH           182  /* Spell Scroll: Death */ 
#define I_B_THUNDERSTORM    183  /* Spell Scroll: Thunder Storm */
 #define I_B_NEGATIS         184  /* Spell Scroll: Negatis */
 #define I_B_EARTHQUAKE      185  /* Spell Scroll: Earthquake */
 #define I_B_PLAGUE          186  /* Spell Scroll: Plague */
 #define I_B_XSURGE          187  /* Spell Scroll: X-Surge */
 #define I_CHENDIGAL         188  /* Chendigal */
 #define I_CHENDIGRA         189  /* Chendigra */
 #define I_DYNAMITE          190  /* Dynamite */

```


:KS:popcorn: I would recommend equipping an item, then scanmem the weapon's
code from the this list (1 - 190).  Next, either remove the item and scanmem
for 0, or equip another item and scanmem its value from this list.  You may
have to do this several times to get the list in your terminal down to 1.
Next, assign the weapon or armor you want.  I would recommend you keep
to weapons and armor specific to the characters.  If you remove a weapon
class not equippable by the character, it will not be available for re-
equipping.  Happy gaming!

---

### Post by erikthedrink on 2010-09-30
To clarify, Mace is a 1, Rapier is a 9, and knife is a 20.  From here, you should be able to see the other number values.:P

---

### Post by erikthedrink on 2010-09-30
Also, here is the source code hyper link
[http://kq.sourcearchive.com/documentation/0.99.cvs20070319-1.1/itemdefs_8h-source.html](http://kq.sourcearchive.com/documentation/0.99.cvs20070319-1.1/itemdefs_8h-source.html)
:guitar:

---

### Post by Ivon365 on 2010-10-03
I am at the tower where I beleive the Oracle is at. I am on the second floor and I see no way to get to the stairs to go up. Would someone please help me?

---

### Post by erikthedrink on 2010-10-08
I don't know the sequence, but you need to keep stepping on the four circular switches.  The path will open slightly on the left side, though it may not appear to.

---

### Post by Raelic on 2010-10-16
> **Above said:**
> Here are the steps you need to follow at this website:

[http://us.generation-nt.com/answer/bug-537798-kq-bug-at-dungar-estate-help-168963471.html](http://us.generation-nt.com/answer/bug-537798-kq-bug-at-dungar-estate-help-168963471.html)

I am using ubuntu 10.04 and these steps fixed the glitch in the game. Just make sure to spell and space everything correctly. It took me 6 tries but it solved the Dungar house bug.


This Didnt work for me at all, game still crashes. Tried following that link but when I was entering the patch URL, I kept getting 404.
So I manually edited the .lua file in gedit, still the same result.
any other suggestions?

---

