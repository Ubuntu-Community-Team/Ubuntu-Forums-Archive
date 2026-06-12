---
title: "Having trouble with make-kpkg and Kernel 2.6.29.1"
date: 2009-04-10
forum: General Help
---

### Post by TremerePuck on 2009-04-10
I used the following command:
```
sudo fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
```
as per this tutorial [http://www.howtoforge.com/kernel_compilation_ubuntu]("http://www.howtoforge.com/kernel_compilation_ubuntu")
And got this error:

```
make[2]: Leaving directory `/usr/src/linux-2.6.29.1'                               
test ! -e scripts/package/builddeb || mv -f scripts/package/builddeb scripts/package/builddeb.kpkg-dist                                                               
test ! -e scripts/package/Makefile || test -f scripts/package/Makefile.kpkg-dist || (mv -f scripts/package/Makefile scripts/package/Makefile.kpkg-dist && (echo "# Dummy file "; echo "help:") >  scripts/package/Makefile)                              
test ! -f Documentation/lguest/lguest ||                             \             
            install -p    -o root -g root  -m  644 Documentation/lguest/lguest /usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom/lib/modules/2.6.29.1-custom/lguest                                                                             
test ! -f /usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom/lib/modules/2.6.29.1-custom/lguest ||            \                                               
            chmod 755 /usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom/lib/modules/2.6.29.1-custom/lguest                                                   
test ! -e /usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom/lib/modules/2.6.29.1-custom/source ||                   \                                        
           mv /usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom/lib/modules/2.6.29.1-custom/source ./debian/source-link                                      
test ! -e /usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom/lib/modules/2.6.29.1-custom/build ||                    \                                        
           mv /usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom/lib/modules/2.6.29.1-custom/build ./debian/build-link                                        
test ! -e ./debian/source-link ||                                              \   
           mv ./debian/source-link /usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom/lib/modules/2.6.29.1-custom/source                                      
test ! -e  ./debian/build-link ||                                              \   
           mv  ./debian/build-link /usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom/lib/modules/2.6.29.1-custom/build                                       
/sbin/depmod -q -FSystem.map -b /usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom 2.6.29.1-custom;                                                           
test ! -f System.map ||  cp System.map                         \                   
                        /usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom//boot/System.map-2.6.29.1-custom;                                                  
test ! -f System.map ||  chmod 644                             \                   
                        /usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom//boot/System.map-2.6.29.1-custom;                                                  
cp arch/x86/boot/bzImage /usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom//boot/vmlinuz-2.6.29.1-custom                                                     
chmod 644 /usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom//boot/vmlinuz-2.6.29.1-custom;                                                                   
if test -d /usr/src/linux-2.6.29.1/debian/image.d ; then                          \
             TMPTOP=/usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom version=2.6.29.1-custom IMAGE_TOP=/usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom   \                                                                          
                   run-parts --verbose /usr/src/linux-2.6.29.1/debian/image.d ;   \
         fi                                                                        
if [ -x debian/post-install ]; then                               \                
                TMPTOP=/usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom STEM=linux version=2.6.29.1-custom       \                                          
                IMAGE_TOP=/usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom debian/post-install;            \                                                
        fi                                                                         
test ! -s applied_patches || cp applied_patches                        \           
                        /usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom//boot/patches-2.6.29.1-custom                                                      
test ! -s applied_patches || chmod 644                                 \           
                        /usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom//boot/patches-2.6.29.1-custom                                                      
test ! -f Kerntypes ||  cp Kerntypes                                   \           
                        /usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom//boot/Kerntypes-2.6.29.1-custom                                                    
test ! -f Kerntypes ||  chmod 644                                      \           
                        /usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom//boot/Kerntypes-2.6.29.1-custom                                                    
====== making target debian/stamp/binary/pre-linux-image-2.6.29.1-custom [new prereqs: linux-image-2.6.29.1-custom]======                                             

This is kernel package version 11.015.
/usr/bin/make -f ./debian/rules debian/stamp/binary/linux-image-2.6.29.1-custom
make[2]: Entering directory `/usr/src/linux-2.6.29.1'                          
====== making target debian/stamp/binary/linux-image-2.6.29.1-custom [new prereqs: ]======                                                                            

This is kernel package version 11.015.
install -p -d -o root -g root  -m  755 /usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom/DEBIAN                                                              
sed -e 's/=V/2.6.29.1-custom/g'    -e 's/=IB//g' \                                 
            -e 's/=ST/linux/g'  -e 's/=R//g' \                                     
            -e 's/=K/bzImage/g'     -e 's/=L/lilo/g'         \                     
            -e 's/=I/YES/g'     -e 's,=D,/boot,g'            \                     
            -e 's/=MD/initramfs-tools (>= 0.53) | yaird (>= 0.0.11) | linux-initramfs-tool, /g'                                 \                                     
            -e 's@=MK@mkinitramfs-kpkg mkinitrd.yaird@g' -e 's@=A@i386@g'   \      
            -e 's@=M@@g'    -e 's/=OF//g'    \                                     
            -e 's/=S//g' -e 's@=B@i386@g'     \                                    
          ./debian/pkg/image/postinst > /usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom/DEBIAN/postinst                                                    
chmod 755 /usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom/DEBIAN/postinst                                                                                  
sed -e 's/=V/2.6.29.1-custom/g'    -e 's/=IB//g' \                                 
            -e 's/=ST/linux/g'  -e 's/=R//g' \                                     
            -e 's/=K/bzImage/g'     -e 's/=L/lilo/g'         \                     
            -e 's/=I/YES/g'     -e 's,=D,/boot,g'            \                     
            -e 's/=MD/initramfs-tools (>= 0.53) | yaird (>= 0.0.11) | linux-initramfs-tool, /g'                                 \                                     
            -e 's@=MK@mkinitramfs-kpkg mkinitrd.yaird@g' -e 's@=A@i386@g'   \      
            -e 's@=M@@g'    -e 's/=OF//g'    \                                     
            -e 's/=S//g'  -e 's@=B@i386@g'    \                                    
         ./debian/pkg/image/config > /usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom/DEBIAN/config                                                         
chmod 755 /usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom/DEBIAN/config 
sed -e 's/=V/2.6.29.1-custom/g'    -e 's/=IB//g' \                                 
            -e 's/=ST/linux/g'  -e 's/=R//g' \                                     
            -e 's/=K/bzImage/g'     -e 's/=L/lilo/g'         \                     
            -e 's/=I/YES/g'     -e 's,=D,/boot,g'            \                     
            -e 's/=MD/initramfs-tools (>= 0.53) | yaird (>= 0.0.11) | linux-initramfs-tool, /g'                                 \                                     
            -e 's@=MK@mkinitramfs-kpkg mkinitrd.yaird@g' -e 's@=A@i386@g'   \      
            -e 's@=M@@g'    -e 's/=OF//g'    \                                     
            -e 's/=S//g' -e 's@=B@i386@g'     \                                    
         ./debian/pkg/image/postrm > /usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom/DEBIAN/postrm                                                         
chmod 755 /usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom/DEBIAN/postrm 
sed -e 's/=V/2.6.29.1-custom/g'    -e 's/=IB//g'           \                       
            -e 's/=ST/linux/g'  -e 's/=R//g' \                                     
            -e 's/=K/bzImage/g'     -e 's/=L/lilo/g'         \                     
            -e 's/=I/YES/g'     -e 's,=D,/boot,g'            \                     
            -e 's/=MD/initramfs-tools (>= 0.53) | yaird (>= 0.0.11) | linux-initramfs-tool, /g'                                 \                                     
            -e 's@=MK@mkinitramfs-kpkg mkinitrd.yaird@g' -e 's@=A@i386@g'   \      
            -e 's@=M@@g'    -e 's/=OF//g'    \                                     
            -e 's/=S//g' -e 's@=B@i386@g'     \
         ./debian/pkg/image/preinst > /usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom/DEBIAN/preinst
chmod 755 /usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom/DEBIAN/preinst
sed -e 's/=V/2.6.29.1-custom/g'    -e 's/=IB//g'    \
            -e 's/=ST/linux/g'  -e 's/=R//g' \
            -e 's/=K/bzImage/g'     -e 's/=L/lilo/g'         \
            -e 's/=I/YES/g'     -e 's,=D,/boot,g'            \
            -e 's/=MD/initramfs-tools (>= 0.53) | yaird (>= 0.0.11) | linux-initramfs-tool, /g'                                 \
            -e 's@=MK@mkinitramfs-kpkg mkinitrd.yaird@g' -e 's@=A@i386@g'   \
            -e 's@=M@@g'    -e 's/=OF//g'    \
            -e 's/=S//g' -e 's@=B@i386@g'     \
         ./debian/pkg/image/prerm > /usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom/DEBIAN/prerm
chmod 755 /usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom/DEBIAN/prerm
po2debconf debian/templates.in > debian/templates.l10n
sed -e 's/=V/2.6.29.1-custom/g'    -e 's/=IB//g'    \
            -e 's/=ST/linux/g'  -e 's/=R//g' \
            -e 's/=K/bzImage/g'     -e 's/=L/lilo/g'          \
            -e 's@=MK@mkinitramfs-kpkg mkinitrd.yaird@g' -e 's@=A@i386@g'   \
            -e 's/=I/YES/g'     -e 's,=D,/boot,g'        \
            -e 's/=MD/initramfs-tools (>= 0.53) | yaird (>= 0.0.11) | linux-initramfs-tool, /g'                                \
            -e 's@=M@@g'    -e 's/=OF//g'    \
            -e 's/=S//g' -e 's@=B@i386@g'     \
         ./debian/templates.l10n   > ./debian/templates.master
install -p    -o root -g root  -m  644 ./debian/templates.master /usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom/DEBIAN/templates
dpkg-gencontrol -DArchitecture=i386 -isp             \
                        -plinux-image-2.6.29.1-custom -P/usr/src/linux-2.6.29.1/debian/linux-image-2.6.29.1-custom/
dpkg-gencontrol: error: package linux-image-2.6.29.1-custom not in control info
make[2]: *** [debian/stamp/binary/linux-image-2.6.29.1-custom] Error 255
make[2]: Leaving directory `/usr/src/linux-2.6.29.1'
make[1]: *** [debian/stamp/binary/pre-linux-image-2.6.29.1-custom] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.29.1'
make: *** [kernel_image] Error 2
```

Any and all help will be greatly appreciated.

---

