---
title: "Can't reinstall compiz or desktop effects..."
date: 2007-09-09
forum: Desktop Effects &amp; Customization
---

### Post by Inkpot on 2007-09-09
See, this is what I get for tinkering....

I successfully installed Beryl and got *some* of the effects to work and saw (on these forums) that I no longer needed compiz or desktop effects - so I removed them using synaptic. Now, I've lost my cube and on a whim, tried to reinstall compiz and desktop effects only to get this message: 

compiz:
 Depends: compiz-decorator  but it is not installable

So now what do I do? Yeah, I know....if it KINDA works...don't fix it! :P




Inkpot

---

### Post by hyperair on 2007-09-09
You sound like you've got Trevino's eyecandy repository enabled. Run this command:
```

cat /etc/apt/sources.list | grep "3v1deb feisty eyecandy"

```
If you have output then you have Trevino's eyecandy repository enabled. In which case you should probably try out Compiz Fusion, which is the merge between Compiz and Beryl. There's a HOWTO floating around somewhere in this forum, go look for it =P

---

### Post by Inkpot on 2007-09-09
Nope...can't install compiz=fusion, either. Get the same type of error message. Is there a certain repository that I need or something?



Inkpot

---

### Post by chuckyp on 2007-09-09
Why would you remove compiz and desktop effects to install beryl to accomplish exactly the same thing?

---

### Post by hyperair on 2007-09-09
@chuckyp: Actually Beryl has quite a few plugins that Desktop Effects lacks, and has a configuration tool.

@Inkpot: I'm assuming you have Trevino's repositories enabled.
1. Remove all Compiz and Desktop Effects packages:
1.1 Open Synaptic
1.2 Run a search for anything with the name compiz
1.3 Mark everything (with compiz in its name) shown for complete removal
1.4 Look for a package called desktop-effects and mark it for complete removal
1.4 Apply

2. Install Compiz Fusion
```
sudo apt-get install compiz compizconfig-settings-manager libcompizconfig-settings-gconf compiz-fusion-*
```

3. Start Compiz Fusion (in the run dialog):
```
compiz --replace -c emerald
```

4. (optional) To make Compiz Fusion start up when you log in, go to System->Preferences->Sessions and look for your beryl-manager entry. Change the command to "compiz --replace -c emerald" and the name to Compiz Fusion or something of that sort.

---

