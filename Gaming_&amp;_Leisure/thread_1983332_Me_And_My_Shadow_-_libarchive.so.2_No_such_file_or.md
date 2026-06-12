---
title: "Me And My Shadow - libarchive.so.2: No such file or directory"
date: 2012-05-20
forum: Gaming &amp; Leisure
---

### Post by mentorious on 2012-05-20
While running Me And My Shadow I see:

```
error while loading shared libraries: libarchive.so.2: cannot open shared object file: No such file or directory
```

So, I turned on synaptic and installed libarchive + libarchive-dev, but the problem is still. Maybe should I copy some library?

---

### Post by Perfect Storm on 2012-05-20
If you're running 64-bit system and the game is 32-bit, you need to install 32-libs.
```
sudo apt-get install ia32-libs
```

---

### Post by mentorious on 2012-05-21
Thx for reply ;)

I have already installed ia32-libs and libarchive12 + libarchive12-dev.

This is interesting..

```
damian@damian-Studio-1749:~$ locate libarchive*
damian@damian-Studio-1749:~$ 

```

I tried reinstall with remove --purge and again install, but no change.

---

### Post by Perfect Storm on 2012-05-21
Try run ldd on the binary and see what it says.

---

### Post by mentorious on 2012-05-21
```
damian@damian-Studio-1749:~/Gry/meandmyshadow-0.3-bin/bin$ ldd meandmyshadow-debian-64
	linux-vdso.so.1 =>  (0x00007fffbd1ff000)
	libSDL-1.2.so.0 => /usr/lib/x86_64-linux-gnu/libSDL-1.2.so.0 (0x00007f3fa580d000)
	libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f3fa55f0000)
	libSDL_ttf-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libSDL_ttf-2.0.so.0 (0x00007f3fa53e9000)
	libSDL_image-1.2.so.0 => /usr/lib/x86_64-linux-gnu/libSDL_image-1.2.so.0 (0x00007f3fa51cc000)
	libSDL_mixer-1.2.so.0 => /usr/lib/x86_64-linux-gnu/libSDL_mixer-1.2.so.0 (0x00007f3fa4f69000)
	libSDL_gfx.so.13 => /usr/lib/x86_64-linux-gnu/libSDL_gfx.so.13 (0x00007f3fa4d51000)
	libcurl.so.4 => /usr/lib/x86_64-linux-gnu/libcurl.so.4 (0x00007f3fa4af4000)
	libarchive.so.2 => not found
	libssl.so.0.9.8 => /lib/x86_64-linux-gnu/libssl.so.0.9.8 (0x00007f3fa48a0000)
	libcrypto.so.0.9.8 => /lib/x86_64-linux-gnu/libcrypto.so.0.9.8 (0x00007f3fa4513000)
	libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007f3fa4213000)
	libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f3fa3f18000)
	libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007f3fa3d02000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f3fa3945000)
	libasound.so.2 => /usr/lib/x86_64-linux-gnu/libasound.so.2 (0x00007f3fa3657000)
	libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f3fa3453000)
	libpulse-simple.so.0 => /usr/lib/x86_64-linux-gnu/libpulse-simple.so.0 (0x00007f3fa324f000)
	libpulse.so.0 => /usr/lib/x86_64-linux-gnu/libpulse.so.0 (0x00007f3fa3006000)
	libX11.so.6 => /usr/lib/x86_64-linux-gnu/libX11.so.6 (0x00007f3fa2cd2000)
	libXext.so.6 => /usr/lib/x86_64-linux-gnu/libXext.so.6 (0x00007f3fa2ac1000)
	libcaca.so.0 => /usr/lib/x86_64-linux-gnu/libcaca.so.0 (0x00007f3fa27f5000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f3fa5ace000)
	libfreetype.so.6 => /usr/lib/x86_64-linux-gnu/libfreetype.so.6 (0x00007f3fa2559000)
	libpng12.so.0 => /lib/x86_64-linux-gnu/libpng12.so.0 (0x00007f3fa2331000)
	libjpeg.so.8 => /usr/lib/x86_64-linux-gnu/libjpeg.so.8 (0x00007f3fa20e1000)
	libtiff.so.4 => /usr/lib/x86_64-linux-gnu/libtiff.so.4 (0x00007f3fa1e7e000)
	libmikmod.so.2 => /usr/lib/x86_64-linux-gnu/libmikmod.so.2 (0x00007f3fa1c31000)
	libvorbisfile.so.3 => /usr/lib/x86_64-linux-gnu/libvorbisfile.so.3 (0x00007f3fa1a28000)
	libFLAC.so.8 => /usr/lib/x86_64-linux-gnu/libFLAC.so.8 (0x00007f3fa17de000)
	libmad.so.0 => /usr/lib/x86_64-linux-gnu/libmad.so.0 (0x00007f3fa15be000)
	libidn.so.11 => /usr/lib/x86_64-linux-gnu/libidn.so.11 (0x00007f3fa138a000)
	liblber-2.4.so.2 => /usr/lib/x86_64-linux-gnu/liblber-2.4.so.2 (0x00007f3fa117c000)
	libldap_r-2.4.so.2 => /usr/lib/x86_64-linux-gnu/libldap_r-2.4.so.2 (0x00007f3fa0f2d000)
	librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007f3fa0d24000)
	libgssapi_krb5.so.2 => /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2 (0x00007f3fa0ae6000)
	libssl.so.1.0.0 => /lib/x86_64-linux-gnu/libssl.so.1.0.0 (0x00007f3fa088a000)
	libcrypto.so.1.0.0 => /lib/x86_64-linux-gnu/libcrypto.so.1.0.0 (0x00007f3fa04c1000)
	librtmp.so.0 => /usr/local/lib/librtmp.so.0 (0x00007f3fa02a7000)
	libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007f3fa0090000)
	libpulsecommon-1.1.so => /usr/lib/x86_64-linux-gnu/libpulsecommon-1.1.so (0x00007f3f9fe31000)
	libjson.so.0 => /usr/lib/x86_64-linux-gnu/libjson.so.0 (0x00007f3f9fc29000)
	libdbus-1.so.3 => /lib/x86_64-linux-gnu/libdbus-1.so.3 (0x00007f3f9f9e4000)
	libxcb.so.1 => /usr/lib/x86_64-linux-gnu/libxcb.so.1 (0x00007f3f9f7c6000)
	libslang.so.2 => /lib/x86_64-linux-gnu/libslang.so.2 (0x00007f3f9f455000)
	libncursesw.so.5 => /lib/x86_64-linux-gnu/libncursesw.so.5 (0x00007f3f9f227000)
	libtinfo.so.5 => /lib/x86_64-linux-gnu/libtinfo.so.5 (0x00007f3f9f000000)
	libvorbis.so.0 => /usr/lib/x86_64-linux-gnu/libvorbis.so.0 (0x00007f3f9edd3000)
	libogg.so.0 => /usr/lib/x86_64-linux-gnu/libogg.so.0 (0x00007f3f9ebcc000)
	libresolv.so.2 => /lib/x86_64-linux-gnu/libresolv.so.2 (0x00007f3f9e9b0000)
	libsasl2.so.2 => /usr/lib/x86_64-linux-gnu/libsasl2.so.2 (0x00007f3f9e794000)
	libgssapi.so.3 => /usr/lib/x86_64-linux-gnu/libgssapi.so.3 (0x00007f3f9e556000)
	libgnutls.so.26 => /usr/lib/x86_64-linux-gnu/libgnutls.so.26 (0x00007f3f9e29a000)
	libgcrypt.so.11 => /lib/x86_64-linux-gnu/libgcrypt.so.11 (0x00007f3f9e01b000)
	libkrb5.so.3 => /usr/lib/x86_64-linux-gnu/libkrb5.so.3 (0x00007f3f9dd4d000)
	libk5crypto.so.3 => /usr/lib/x86_64-linux-gnu/libk5crypto.so.3 (0x00007f3f9db25000)
	libcom_err.so.2 => /lib/x86_64-linux-gnu/libcom_err.so.2 (0x00007f3f9d920000)
	libkrb5support.so.0 => /usr/lib/x86_64-linux-gnu/libkrb5support.so.0 (0x00007f3f9d718000)
	libwrap.so.0 => /lib/x86_64-linux-gnu/libwrap.so.0 (0x00007f3f9d50e000)
	libsndfile.so.1 => /usr/lib/x86_64-linux-gnu/libsndfile.so.1 (0x00007f3f9d2a7000)
	libasyncns.so.0 => /usr/lib/x86_64-linux-gnu/libasyncns.so.0 (0x00007f3f9d0a1000)
	libXau.so.6 => /usr/lib/x86_64-linux-gnu/libXau.so.6 (0x00007f3f9ce9d000)
	libXdmcp.so.6 => /usr/lib/x86_64-linux-gnu/libXdmcp.so.6 (0x00007f3f9cc97000)
	libheimntlm.so.0 => /usr/lib/x86_64-linux-gnu/libheimntlm.so.0 (0x00007f3f9ca90000)
	libkrb5.so.26 => /usr/lib/x86_64-linux-gnu/libkrb5.so.26 (0x00007f3f9c809000)
	libasn1.so.8 => /usr/lib/x86_64-linux-gnu/libasn1.so.8 (0x00007f3f9c569000)
	libhcrypto.so.4 => /usr/lib/x86_64-linux-gnu/libhcrypto.so.4 (0x00007f3f9c335000)
	libroken.so.18 => /usr/lib/x86_64-linux-gnu/libroken.so.18 (0x00007f3f9c11f000)
	libtasn1.so.3 => /usr/lib/x86_64-linux-gnu/libtasn1.so.3 (0x00007f3f9bf0e000)
	libp11-kit.so.0 => /usr/lib/x86_64-linux-gnu/libp11-kit.so.0 (0x00007f3f9bcfc000)
	libgpg-error.so.0 => /lib/x86_64-linux-gnu/libgpg-error.so.0 (0x00007f3f9baf7000)
	libkeyutils.so.1 => /lib/x86_64-linux-gnu/libkeyutils.so.1 (0x00007f3f9b8f3000)
	libnsl.so.1 => /lib/x86_64-linux-gnu/libnsl.so.1 (0x00007f3f9b6d8000)
	libvorbisenc.so.2 => /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2 (0x00007f3f9b209000)
	libwind.so.0 => /usr/lib/x86_64-linux-gnu/libwind.so.0 (0x00007f3f9afe0000)
	libheimbase.so.1 => /usr/lib/x86_64-linux-gnu/libheimbase.so.1 (0x00007f3f9add0000)
	libhx509.so.5 => /usr/lib/x86_64-linux-gnu/libhx509.so.5 (0x00007f3f9ab86000)
	libsqlite3.so.0 => /usr/lib/x86_64-linux-gnu/libsqlite3.so.0 (0x00007f3f9a8e3000)
	libcrypt.so.1 => /lib/x86_64-linux-gnu/libcrypt.so.1 (0x00007f3f9a6a9000)
```

Look there, only this not found:
```
libarchive.so.2 => not found
```

This library isn't in my system, but all packages, which her containing  (libarchive, libarchive-dev) are installed. So, what's wrong?

I will search her in internet and manually paste to /usr/lib, I'm waiting for more suggestions and sorry for my badly english ( ubuntu user from Czech) ;)

---

### Post by Perfect Storm on 2012-05-21
It seems that the game run 64-bit so it's not a 32-bit compatible problem. It could be that it's looking for the lib under a different name. To solve this you need to find the file that looks like it and symblink it with the lib it's looking for.

---

### Post by Perfect Storm on 2012-05-21
Sorry for the double post.

If you're looking via Synaptic Package manager for libarchieve ( libarchive12) you'll see under 'installed files' that the package installed a lib called '/usr/lib/x86_64-linux-gnu/libarchive.so.12'

Try symblink it.

```
sudo ln -s /usr/lib/x86_64-linux-gnu/libarchive.so.12 /usr/lib/x86_64-linux-gnu/libarchive.so.2
```

---

### Post by mentorious on 2012-05-21
Now work, thanks! ;)

---

