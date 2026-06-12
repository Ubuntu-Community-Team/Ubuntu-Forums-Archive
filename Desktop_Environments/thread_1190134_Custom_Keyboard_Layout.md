---
title: "Custom Keyboard Layout"
date: 2009-06-17
forum: Desktop Environments
---

### Post by aktiv on 2009-06-17
Hi

Ok, so I'm trying to set up a custom keyboard layout .. what I've done so far is .. :

added a new entry in /usr/share/X11/xkb/symbols/no
short version here:

partial alphanumeric_keys       
xkb_symbols "loke" {            
        name[Group1] = "Norway - Loke Custom";
        include "level3(ralt_switch)"         
        include "us(dvorak)"                  
        key <AB01> { [             ae,             AE,     Greek_zeta,          U2286 ] };
        key <AB02> { [              q,              Q,      Greek_chi,          U2287 ] };
        key <AB03> { [              j,              J,    Greek_theta,    Greek_THETA ] };
        key <AB04> { [              k,              K,      Greek_phi,      Greek_PHI ] };
        etc etc
};

then I added a new entry in /usr/share/X11/xkb/symbols.dir
that looks like this:
--p----- a------- no(loke)

and then I added in /etc/X11/xkb/base.xml:

    <layout>                                                
      <configItem>                                          
        <name>no</name>                                     
        <shortDescription>Nor</shortDescription>            
        <description>Norway</description>                   
        <languageList><iso639Id>nor</iso639Id></languageList>
      </configItem>                                          
      <variantList>                                          
                                            
        <variant>              // DVORAK VARIANT AS EXAMPLE                                     
          <configItem>                                       
            <name>dvorak</name>                              
            <description>Dvorak</description>                
          </configItem>                                      
        </variant>                                           
                                                       
        <variant>             // MY VARIANT ENTRY                                               
          <configItem>                                                       
            <name>loke</name>                                                 
            <description>Loke Custom Dvorak</description>                     
          </configItem>                                                       
        </variant>
                                                            
      </variantList>                                                          
    </layout> 

Now, I hoped that after this and a reboot I could go System > Preferences > Keyboard > Layouts > Add > Country: Norway and find "Loke Custom Dvorak" under variants, but nooo :)

So, what more do I need to do here, or how am I supposed to do this?

Ubuntu 9.04: Linux 2.6.28-11-generic #42-Ubuntu SMP x86_64 GNU/Linux
All files edited are linked with ln -s from ~/.root/<OriginalDIRS>/

Tx

---

