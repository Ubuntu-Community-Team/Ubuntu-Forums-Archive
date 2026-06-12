---
title: "gdesklets startup error"
date: 2005-11-22
forum: Desktop Environments
---

### Post by dcherryholmes on 2005-11-22
Hi all.  First post, but not a complete newb.  I spent the last couple of years on gentoo, but I recently tried Ubuntu and got hooked.  Here's my problem:  when I start gdesklets (running just the toolbar app), I get the following error on startup:

coercing to Unicode: need string or buffer, float found                              
/usr/share/gdesklets/Sensors/BSRDGborder/__init__.py                                 
  136           output.set ( "bordershowbottomright", bordershowbottom and           
bordershowright )                                                                    
  137                                                                                
  138           #Container boundaries                                                
  139           containerleft = borderthickness * bordershowleft                     
  140           containertop = borderthickness * bordershowtop                       
> 141           containerwidth = containercontentwidth + ( self.get_config (         
"containerhpadding" ) * 2.0 ) + ( self.get_config ( "bghpadding" ) * 2.0 )           
  142           containerheight = self.get_config ( "containercontentheight" ) + (   
self.get_config ( "containervpadding" ) * 2.0 ) + ( self.get_config ( "bgvpadding" ) 
* 2.0 )                                                                              
  143           output.set ( "containerleft", containerleft )                        
  144           output.set ( "containertop", containertop )                          
  145           output.set ( "containerright", containerleft + containerwidth )      
  146           output.set ( "containerbottom", containertop + containerheight )     
  147           output.set ( "containerwidth", containerwidth )          

Checking the "ignore this error" fails to prevent getting the notification, but otherwise the toolbar seems to function fine.  I've searched the forums and did some googling, but I didn't find any answers.  The error is related to lines 141 and 142.  I tweaked that file myself, replacing the 2's with 2.0's, in the naive hope that switching from a float to an integer might jiggle things into place, but it had no affect other than to replace complaining about an int to complaining about a float.  Any suggestions?

---

