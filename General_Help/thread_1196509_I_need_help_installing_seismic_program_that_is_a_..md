---
title: "I need help installing seismic program that is a .tar file     I am desperate."
date: 2009-06-25
forum: General Help
---

### Post by ftgibson on 2009-06-25
I have a program called hyposat.4_4b.tar and I can not install it. My mentor was killed in a car accident last year and I am just now trying to install this software  on my home computers in order to find epicenters of local earthquakes.   I am familiar with the Linux platform ie SuSE and Ubuntu but I have never installed a .tar file on my own.  Please help me because I am totally frustrated and tired of messing with it.


Sincerely,
Amie
:confused:

---

### Post by cariboo on 2009-06-25
Welcome to the forums. If you could provide a link to the file it would help quite a bit. To extract the file just double click it, and file roller will open it. Tell it where to extract the file. There should be a readme or install file inside the archive. This should tell you how to install the program.

---

### Post by ftgibson on 2009-06-25
Hi,
    The path to the file I need to open and install is

 /ftgibson/Documents/transfers/hyposat/hyposat.4_4b.tar   

Is this what you are needing?

Many thanks,
Amie

---

### Post by michy99 on 2009-06-25
I think he was asking for a link on the internet where someone could download the file and take a look at it.

Have you extracted the file yet? You should be able to do this by double-clicking on it. Then look in the folder and see if there is a readme file.

---

### Post by geirha on 2009-06-25
To start, list the content of the archive. As of yet, we have no idea if this is source code that needs to be compiled, or if it contains pre-built binaries, or maybe something else.
```
tar tf ~/Documents/transfers/hyposat/hyposat.4_4b.tar
```

---

### Post by ftgibson on 2009-06-25
[EMAIL="OK.ftgibson@ftgibson:%7E$"]ftgibson@ftgibson:~$[/EMAIL] tar tf ~/Documents/transfers/hyposat/hyposat.4_4b.tar
  data/                                                                     
  data/ak135.hed                                                            
  data/elcordir.tbl                                                         
  data/iasp91.hed                                                           
  data/iasp91a.hed                                                          
  data/jb.hed                                                               
  data/prem.hed                                                             
  data/sp6.hed                                                              
  data/ak135.tbl                                                            
  data/REG_L3.DAT                                                           
  data/iasp91.tbl                                                           
  data/iasp91a.tbl                                                          
  data/jb.tbl                                                               
  data/prem.tbl                                                             
  data/sp6.tbl                                                              
  data/stations.dat                                                         
  data/README                                                               
  data/CNelevatio                                                           
  data/CNtype                                                               
  data/CNtype_key                                                           
  data/MB_G-R.DAT                                                           
  data/MB_V-C.DAT                                                           
  data_l/                                                                   
  data_l/README                                                             
  data_l/ak135.tbl                                                          
  data_l/stations.dat                                                       
  data_l/CNtype                                                             
  data_l/elcordir.tbl                                                       
  data_l/CNelevatio                                                         
  data_l/iasp91.tbl                                                         
  data_l/iasp91a.tbl                                                        
  data_l/jb.tbl                                                             
  data_l/prem.tbl                                                           
  data_l/sp6.tbl                                                            
  data_l/ak135.hed                                                          
  data_l/CNtype_key                                                         
  data_l/MB_G-R.DAT                                                         
  data_l/MB_V-C.DAT                                                         
  data_l/iasp91.hed                                                         
  data_l/iasp91a.hed                                                        
  data_l/jb.hed                                                             
  data_l/prem.hed                                                           
  data_l/sp6.hed                                                            
  data_l/REG_L3.DAT                                                         
  man/                                                                      
  man/hyposat_man.pdf                                                       
  man/schweitzer_1997.pdf                                                   
  src/                                                                      
  src/Makefile                                                              
  src/hyposat.f                                                             
  src/hyposat_cross.f                                                       
  src/hyposat_geo.f                                                         
  src/hyposat_gmi.f                                                         
  src/hyposat_lib.f                                                         
  src/hyposat_name.f                                                        
  src/hyposat_time.f                                                        
  src/hypomod.f                                                             
  src/hyposat.o                                                             
  src/libtau_h.o                                                            
  src/cgmi.h                                                                
  src/hyposat_lib.o                                                         
  src/hyposat_geo.o                                                         
  src/hyposat_name.o                                                        
  src/hyposat_clib.o                                                        
  src/hyposat_clib.c                                                        
  src/hyposat_loc.o                                                         
  src/hyposat_crust.o                                                       
  src/hyposat_mag.o                                                         
  src/libtau_h.f                                                            
  src/ttlim.h                                                               
  src/hyposat_cross.o                                                       
  src/hyposat_crust_mod.o                                                   
  src/hyposat_crust.f                                                       
  src/hyposat_crust_mod.f                                                   
  src/hyposat_file.f                                                        
  src/hyposat_loc.f                                                         
  src/hyposat_mag.f                                                         
  src/hyposat_time.o                                                        
  src/hyposat_gmi.o                                                         
  src/hyposat_file.o                                                        
  src/hypomod.o                                                             
  src/Makefile.hypomod                                                      
  src/magpar.h                                                              
  src/ttimes.h                                                              
  src_l/                                                                    
  src_l/cgmi.h                                                              
  src_l/hypomod.f                                                           
  src_l/hyposat.o                                                           
  src_l/hyposat.f                                                           
  src_l/libtau_h.o                                                          
  src_l/hyposat_clib.c                                                      
  src_l/hyposat_lib.o                                                       
  src_l/hyposat_cross.f                                                     
  src_l/hyposat_geo.o                                                       
  src_l/hyposat_crust.f                                                     
  src_l/hyposat_name.o                                                      
  src_l/hyposat_crust_mod.f                                                 
  src_l/hyposat_clib.o                                                      
  src_l/hyposat_file.f                                                      
  src_l/hyposat_loc.o                                                       
  src_l/hyposat_geo.f                                                       
  src_l/hyposat_crust.o                                                     
  src_l/hyposat_gmi.f                                                       
  src_l/hyposat_mag.o                                                       
  src_l/hyposat_lib.f                                                       
  src_l/hyposat_cross.o                                                     
  src_l/hyposat_loc.f                                                       
  src_l/hyposat_time.o                                                      
  src_l/hyposat_mag.f                                                       
  src_l/hyposat_gmi.o                                                       
  src_l/hyposat_name.f                                                      
  src_l/hyposat_file.o                                                      
  src_l/hyposat_time.f                                                      
  src_l/hyposat_crust_mod.o                                                 
  src_l/libtau_h.f                                                          
  src_l/hypomod.o                                                           
  src_l/magpar.h                                                            
  src_l/Makefile                                                            
  src_l/Makefile.hypomod                                                    
  src_l/ttimes.h                                                            
  src_l/ttlim.h                                                             
  bin/                                                                      
  bin/hyposat                                                               
  bin/hypomod                                                               
  bin_l/                                                                    
  bin_l/hyposat                                                             
  bin_l/hypomod                                                             
  examples/                                                                 
  examples/README                                                           
  examples/loc.dat                                                          
  examples/hyposat-in.net                                                   
  examples/hyposat-in.tele                                                  
  examples/hyposat-in.regional
  examples/hyposat-in.single_array
  examples/hyposat-parameter.tele
  examples/hyposat-parameter.net
  examples/hyposat-parameter.regional
  examples/hyposat-parameter.single_array
  examples/stations.cor
  examples/hyposat-parameter.mod
  examples/hypomod-out.tele
  examples/hyposat-out.single_array
  examples/hyposat-out.tele
  examples/hyposat-out.net
  examples/hyposat-out.regional
  examples_l/
  examples_l/README
  examples_l/loc.dat
  examples_l/hyposat-in.net
  examples_l/hyposat-in.tele
  examples_l/hyposat-in.regional
  examples_l/hyposat-in.single_array
  examples_l/hyposat-parameter.tele
  examples_l/hyposat-out.single_array
  examples_l/hyposat-parameter.net
  examples_l/hyposat-parameter.regional
  examples_l/hyposat-parameter.single_array
  examples_l/stations.cor
  examples_l/hyposat-parameter.mod
  examples_l/hypomod-out.tele
  examples_l/hyposat-out.net
  examples_l/hyposat-out.regional
  examples_l/hyposat-out.tele
  README
  README_l
  README_u
   
  I have tried the "read me" files and have not found much info but I would be happy to post them here if it might be helpful.


Thanks everyone for your help.
Amie

---

### Post by michy99 on 2009-06-25
I found a copy of the tar file and downloaded it. It is fortran77 source code. You might get more help with compiling it in the programming forum.

_[Programming Forum]("http://ubuntuforums.org/forumdisplay.php?f=39")_

---

### Post by geirha on 2009-06-25
Found it too. There's no accompanying licensing information though, but I assume since the source is available on the internet, it's free to use.

Anyway, to compile it, you'll need the packages build-essential and g77.
```
sudo aptitude install build-essential g77
```

Then extract it somewhere in your home folder
```
mkdir ~/hyposat
cd ~/hyposat
tar xf ~/Documents/transfers/hyposat/hyposat.4_4b.tar

```

To build, you want to enter the src_l directory and run make
```
cd src_l
make

```

You should now find the binaries in ~/hyposat/bin_l

---

