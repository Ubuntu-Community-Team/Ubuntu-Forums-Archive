---
title: "Cannot  install ANN package  on scilab 5.1.1"
date: 2010-07-13
forum: Education &amp; Science
---

### Post by OnlyTrouble on 2010-07-13
Hi, 

I downloaded the ANN package and followed the direction in the install.txt file.
Questions:
Which file needs to be edited on the <HOME>/.scilab? and which line should be changed? and to what? should is say exec("builder.sce")?
So after I rn the builder.sce command which went fine 
I typed 
exec ("loader.sce") this is  what I get :
> 
genlib: Warning: Error in file /home/alon/scilab/ANN/ANN_Toolbox_0.4.2/macros/ann/ann_FF_SSAB_online_nb.sci : endfunction is missing.. File ignored
genlib: Warning: Error in file /home/alon/scilab/ANN/ANN_Toolbox_0.4.2/macros/ann/ann_FF_SSAB_batch.sci : endfunction is missing.. File ignored
%helps=[%helps;manp,"Artificial Neural Networks"]
          !--error 4 
Undefined variable: %helps

at line       9 of exec file called by :    
 Clearly something is wrong here.
What do I do
I am running scilab 5.1.1
on openSUSE 11.1
Thanks
 




---

