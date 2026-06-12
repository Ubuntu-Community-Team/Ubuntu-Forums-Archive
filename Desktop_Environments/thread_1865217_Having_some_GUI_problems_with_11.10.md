---
title: "Having some GUI problems with 11.10"
date: 2011-10-19
forum: Desktop Environments
---

### Post by Godsrycht on 2011-10-19
I creamed my pants when I saw the update, updated and now I have almost no GUI. I see my desktop and I have the options File, Edit, View, Go, Bookmarks, Help but nothing else. No task bar on the left side, no icons in the upper right hand corner to control web functions, network functions, time, mail, and reset as I'm used to its just blank. I cant run my terminal to save my life and I'm honestly at a bit of a loss. Help me out here. Should be a copy of my desktop to show you what I'm talking about.

---

### Post by ARooster on 2011-10-19
Try pressing Ctrl+Alt+T to launch a terminal window, then you can try and reset Unity by entering the command
>unity --reset
into the prompt.

---

### Post by Godsrycht on 2011-10-19
I typed that in and got to a part in the terminal then it just stopped here's what I got back from terminal.
```

~$ unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...yes
[LOG]: Moving Internal Files
[LOG]: Copying subdirectory from /home/exelsior/.compiz/session to /home/exelsior/.compiz-1/session
[LOG]: Copied file /home/exelsior/.compiz/session/10b8c7c034235f0678131018783324174400000013830033 to /home/exelsior/.compiz-1/session/10b8c7c034235f0678131018783324174400000013830033
[LOG]: Copied file /home/exelsior/.compiz/session/106e11b214fad8d7a0131023055967748400000013990033 to /home/exelsior/.compiz-1/session/106e11b214fad8d7a0131023055967748400000013990033
[LOG]: Copied file /home/exelsior/.compiz/session/10ba7e10bebf6b5210131023245974862800000013650033 to /home/exelsior/.compiz-1/session/10ba7e10bebf6b5210131023245974862800000013650033
[LOG]: Copied file /home/exelsior/.compiz/session/10e611e1b8d1dfa0cb130447070283894500000041740032 to /home/exelsior/.compiz-1/session/10e611e1b8d1dfa0cb130447070283894500000041740032
[LOG]: Copied file /home/exelsior/.compiz/session/10dd0a977fa412535a131794389465889800000014580033 to /home/exelsior/.compiz-1/session/10dd0a977fa412535a131794389465889800000014580033
[LOG]: Copied file /home/exelsior/.compiz/session/108faf5e750c24de1130474177290630100000013350032 to /home/exelsior/.compiz-1/session/108faf5e750c24de1130474177290630100000013350032
[LOG]: Copied file /home/exelsior/.compiz/session/109762c32c1c2a11a130412613378388600000014180032 to /home/exelsior/.compiz-1/session/109762c32c1c2a11a130412613378388600000014180032
[LOG]: Copied file /home/exelsior/.compiz/session/10bed209a2d48098bf131015806938403100000014210033 to /home/exelsior/.compiz-1/session/10bed209a2d48098bf131015806938403100000014210033
[LOG]: Copied file /home/exelsior/.compiz/session/10df64cdaf4e195e69131603849099574300000014480033 to /home/exelsior/.compiz-1/session/10df64cdaf4e195e69131603849099574300000014480033
[LOG]: Copied file /home/exelsior/.compiz/session/10a42c4247deacefb2131615636889438600000023310033 to /home/exelsior/.compiz-1/session/10a42c4247deacefb2131615636889438600000023310033
[LOG]: Copied file /home/exelsior/.compiz/session/105c3b64c96b880763131616749463369300000015060033 to /home/exelsior/.compiz-1/session/105c3b64c96b880763131616749463369300000015060033
[LOG]: Copied file /home/exelsior/.compiz/session/10f6e2943d8e036498131765418516913900000014580033 to /home/exelsior/.compiz-1/session/10f6e2943d8e036498131765418516913900000014580033
[LOG]: Copied file /home/exelsior/.compiz/session/10242ef96c460c0ad4131517107921545500000014520033 to /home/exelsior/.compiz-1/session/10242ef96c460c0ad4131517107921545500000014520033
[LOG]: Copied file /home/exelsior/.compiz/session/1023a8cad73bff3e6b130847637117279600000013550032 to /home/exelsior/.compiz-1/session/1023a8cad73bff3e6b130847637117279600000013550032
[LOG]: Copied file /home/exelsior/.compiz/session/10652c28e4cf5998e3131673913437965900000015220033 to /home/exelsior/.compiz-1/session/10652c28e4cf5998e3131673913437965900000015220033
[LOG]: Copied file /home/exelsior/.compiz/session/107a5ce54033b41dd6130627593182485900000013180032 to /home/exelsior/.compiz-1/session/107a5ce54033b41dd6130627593182485900000013180032
[LOG]: Copied file /home/exelsior/.compiz/session/10768b5acb246c1d74130759637488207500000013990032 to /home/exelsior/.compiz-1/session/10768b5acb246c1d74130759637488207500000013990032
[LOG]: Copied file /home/exelsior/.compiz/session/105fe2a5786622e4ab131031770034948200000014080033 to /home/exelsior/.compiz-1/session/105fe2a5786622e4ab131031770034948200000014080033
[LOG]: Copied file /home/exelsior/.compiz/session/10176fdb7f6dc4ad78131049542680584700000014140033 to /home/exelsior/.compiz-1/session/10176fdb7f6dc4ad78131049542680584700000014140033
[LOG]: Copied file /home/exelsior/.compiz/session/10a5fd42a794dba296131557979412800900000014750033 to /home/exelsior/.compiz-1/session/10a5fd42a794dba296131557979412800900000014750033
[LOG]: Copied file /home/exelsior/.compiz/session/10169d12c4fd09aef7131887513060335000000014610033 to /home/exelsior/.compiz-1/session/10169d12c4fd09aef7131887513060335000000014610033
[LOG]: Copied file /home/exelsior/.compiz/session/1041c7602172c12825130970574339037700000013410033 to /home/exelsior/.compiz-1/session/1041c7602172c12825130970574339037700000013410033
[LOG]: Copied file /home/exelsior/.compiz/session/1030e65846ef75011213113710104825400000014390033 to /home/exelsior/.compiz-1/session/1030e65846ef75011213113710104825400000014390033
[LOG]: Copied file /home/exelsior/.compiz/session/109d89bfa9c3296a8f130885053579209400000013680032 to /home/exelsior/.compiz-1/session/109d89bfa9c3296a8f130885053579209400000013680032
[LOG]: Copied file /home/exelsior/.compiz/session/102e40f2578a8bfb3d130818809952215500000013620032 to /home/exelsior/.compiz-1/session/102e40f2578a8bfb3d130818809952215500000013620032
[LOG]: Copied file /home/exelsior/.compiz/session/106b71b0c4c974314a130830531073471500000013660032 to /home/exelsior/.compiz-1/session/106b71b0c4c974314a130830531073471500000013660032
[LOG]: Copied file /home/exelsior/.compiz/session/10b39f75a9214c0aca131552550327888000000014230033 to /home/exelsior/.compiz-1/session/10b39f75a9214c0aca131552550327888000000014230033
[LOG]: Copied file /home/exelsior/.compiz/session/1066f9de23f723bc80130542112395803100000013370032 to /home/exelsior/.compiz-1/session/1066f9de23f723bc80130542112395803100000013370032
[LOG]: Copied file /home/exelsior/.compiz/session/107a89e4ebf62fded9131488073067406200000014650033 to /home/exelsior/.compiz-1/session/107a89e4ebf62fded9131488073067406200000014650033
[LOG]: Copied file /home/exelsior/.compiz/session/10e5f410ba1ae3f5130808209399511000000013530032 to /home/exelsior/.compiz-1/session/10e5f410ba1ae3f5130808209399511000000013530032
[LOG]: Copied file /home/exelsior/.compiz/session/10cc1214627677ab7a131596574641911000000014300033 to /home/exelsior/.compiz-1/session/10cc1214627677ab7a131596574641911000000014300033
[LOG]: Copied file /home/exelsior/.compiz/session/1041f6e3142b9bb865131543241397882100000014140033 to /home/exelsior/.compiz-1/session/1041f6e3142b9bb865131543241397882100000014140033
[LOG]: Copied file /home/exelsior/.compiz/session/10b730d06c722c5bb5131058166735395100000013860033 to /home/exelsior/.compiz-1/session/10b730d06c722c5bb5131058166735395100000013860033
[LOG]: Copied file /home/exelsior/.compiz/session/10627614cf9fb2ad0413102381454628600000013700033 to /home/exelsior/.compiz-1/session/10627614cf9fb2ad0413102381454628600000013700033
[LOG]: Copied file /home/exelsior/.compiz/session/10da4412ff4d3f9701130617567050875500000014200032 to /home/exelsior/.compiz-1/session/10da4412ff4d3f9701130617567050875500000014200032
[LOG]: Copied file /home/exelsior/.compiz/session/10851c26dde8fc8131585884120056500000013960033 to /home/exelsior/.compiz-1/session/10851c26dde8fc8131585884120056500000013960033
[LOG]: Copied file /home/exelsior/.compiz/session/106d0df4399e903670131026083542212000000013990033 to /home/exelsior/.compiz-1/session/106d0df4399e903670131026083542212000000013990033
[LOG]: Copied file /home/exelsior/.compiz/session/10175997676afa462f130522703357402200000013700032 to /home/exelsior/.compiz-1/session/10175997676afa462f130522703357402200000013700032
[LOG]: Copied file /home/exelsior/.compiz/session/10215064d459166dae131045950423290200000014020033 to /home/exelsior/.compiz-1/session/10215064d459166dae131045950423290200000014020033
[LOG]: Copied file /home/exelsior/.compiz/session/10d0d33116cf94acf013125861678272100000014220033 to /home/exelsior/.compiz-1/session/10d0d33116cf94acf013125861678272100000014220033
[LOG]: Copied file /home/exelsior/.compiz/session/10541d2299cd178f16131836389762447700000014830033 to /home/exelsior/.compiz-1/session/10541d2299cd178f16131836389762447700000014830033
[LOG]: Copied file /home/exelsior/.compiz/session/10907cc651e223fd3d130804536823577300000013910032 to /home/exelsior/.compiz-1/session/10907cc651e223fd3d130804536823577300000013910032
[LOG]: Copied file /home/exelsior/.compiz/session/105b2a26d8e1567992130811432181394200000013590032 to /home/exelsior/.compiz-1/session/105b2a26d8e1567992130811432181394200000013590032
[LOG]: Copied file /home/exelsior/.compiz/session/103e2af83e5852f5a513072598498959700000013840032 to /home/exelsior/.compiz-1/session/103e2af83e5852f5a513072598498959700000013840032
[LOG]: Copied file /home/exelsior/.compiz/session/104e4e2d829bf584fa130549488170647200000013390032 to /home/exelsior/.compiz-1/session/104e4e2d829bf584fa130549488170647200000013390032
[LOG]: Copied file /home/exelsior/.compiz/session/109105bc212d09cd92130726876413499400000013570032 to /home/exelsior/.compiz-1/session/109105bc212d09cd92130726876413499400000013570032
[LOG]: Copied file /home/exelsior/.compiz/session/10f93d2df04a04e41b131594599658927200000014590033 to /home/exelsior/.compiz-1/session/10f93d2df04a04e41b131594599658927200000014590033
[LOG]: Copied file /home/exelsior/.compiz/session/104b5d9d035eeff5cc131568276457251800000014660033 to /home/exelsior/.compiz-1/session/104b5d9d035eeff5cc131568276457251800000014660033
[LOG]: Copied file /home/exelsior/.compiz/session/10d9eac2c5e0a6d54f130833734871516200000052230032 to /home/exelsior/.compiz-1/session/10d9eac2c5e0a6d54f130833734871516200000052230032
[LOG]: Copied file /home/exelsior/.compiz/session/101e3bcfdf2f8da044130934485628281700000014240033 to /home/exelsior/.compiz-1/session/101e3bcfdf2f8da044130934485628281700000014240033
[LOG]: Copied file /home/exelsior/.compiz/session/10ae14879021c6f69d13086920554437400000013490032 to /home/exelsior/.compiz-1/session/10ae14879021c6f69d13086920554437400000013490032
[LOG]: Copied file /home/exelsior/.compiz/session/10c8eef4d8f11b2e41130790328416578600000014350032 to /home/exelsior/.compiz-1/session/10c8eef4d8f11b2e41130790328416578600000014350032
[LOG]: Copied file /home/exelsior/.compiz/session/1020a04ab9456c08b9131895052836315800000018110033 to /home/exelsior/.compiz-1/session/1020a04ab9456c08b9131895052836315800000018110033
[LOG]: Copied file /home/exelsior/.compiz/session/10abebf86cf4ef9cc130874431478839000000013660032 to /home/exelsior/.compiz-1/session/10abebf86cf4ef9cc130874431478839000000013660032
[LOG]: Copied file /home/exelsior/.compiz/session/10b31632baf9ca86cd131041843231517900000014220033 to /home/exelsior/.compiz-1/session/10b31632baf9ca86cd131041843231517900000014220033
[LOG]: Copied file /home/exelsior/.compiz/session/10509b8f9c8aff9daf130965220293262800000013590033 to /home/exelsior/.compiz-1/session/10509b8f9c8aff9daf130965220293262800000013590033
[LOG]: Copied file /home/exelsior/.compiz/session/10c376920cdae0e159131290012629008800000015110033 to /home/exelsior/.compiz-1/session/10c376920cdae0e159131290012629008800000015110033
[LOG]: Copied file /home/exelsior/.compiz/session/101efc98e7d9bf25b1130964946514890500000013750033 to /home/exelsior/.compiz-1/session/101efc98e7d9bf25b1130964946514890500000013750033
[LOG]: Copied file /home/exelsior/.compiz/session/10a60d7878d8baa95131680535698323300000014520033 to /home/exelsior/.compiz-1/session/10a60d7878d8baa95131680535698323300000014520033
[LOG]: Copied file /home/exelsior/.compiz/session/107d7c551e16ed9060131104563615000900000042930033 to /home/exelsior/.compiz-1/session/107d7c551e16ed9060131104563615000900000042930033
[LOG]: Copied file /home/exelsior/.compiz/session/10af65a1f5dc855eb131309200629547700000014310033 to /home/exelsior/.compiz-1/session/10af65a1f5dc855eb131309200629547700000014310033
[LOG]: Copied file /home/exelsior/.compiz/session/107db1b3d46fd1ed9131103198870590500000014240033 to /home/exelsior/.compiz-1/session/107db1b3d46fd1ed9131103198870590500000014240033
[LOG]: Copied file /home/exelsior/.compiz/session/1024c0abdbfa2ac0a5131111333177145500000014970033 to /home/exelsior/.compiz-1/session/1024c0abdbfa2ac0a5131111333177145500000014970033
[LOG]: Copied file /home/exelsior/.compiz/session/1043d44d6657290d92131153646415619300000014650033 to /home/exelsior/.compiz-1/session/1043d44d6657290d92131153646415619300000014650033
[LOG]: Copied file /home/exelsior/.compiz/session/1023e885cafe0b5d06131104257040197300000014070033 to /home/exelsior/.compiz-1/session/1023e885cafe0b5d06131104257040197300000014070033
[LOG]: Copied file /home/exelsior/.compiz/session/105fa438f921645759131104310527662200000014050033 to /home/exelsior/.compiz-1/session/105fa438f921645759131104310527662200000014050033
[LOG]: Copied file /home/exelsior/.compiz/session/10e2d20572d1d1631131145363262664200000014730033 to /home/exelsior/.compiz-1/session/10e2d20572d1d1631131145363262664200000014730033
[LOG]: Copied file /home/exelsior/.compiz/session/104adc6cd0a65cb666131149838013091600000016570033 to /home/exelsior/.compiz-1/session/104adc6cd0a65cb666131149838013091600000016570033
[LOG]: Copied file /home/exelsior/.compiz/session/103eaf5567cb5845d9131162504227041600000014500033 to /home/exelsior/.compiz-1/session/103eaf5567cb5845d9131162504227041600000014500033
[LOG]: Copied file /home/exelsior/.compiz/session/10923bb906e6fd641131113763745080500000014200033 to /home/exelsior/.compiz-1/session/10923bb906e6fd641131113763745080500000014200033
[LOG]: Copied file /home/exelsior/.compiz/session/1026121c2ca53ceca7131367930810804800000016380033 to /home/exelsior/.compiz-1/session/1026121c2ca53ceca7131367930810804800000016380033
[LOG]: Copied file /home/exelsior/.compiz/session/1081a07ebf73fba04a131389183643349000000015830033 to /home/exelsior/.compiz-1/session/1081a07ebf73fba04a131389183643349000000015830033
[LOG]: Copied file /home/exelsior/.compiz/session/1016d9d03841814158131255576572060800000014560033 to /home/exelsior/.compiz-1/session/1016d9d03841814158131255576572060800000014560033
[LOG]: Copied file /home/exelsior/.compiz/session/10e148dbc4e7a27b06131258574841325100000014030033 to /home/exelsior/.compiz-1/session/10e148dbc4e7a27b06131258574841325100000014030033
[LOG]: Copied file /home/exelsior/.compiz/session/105e8a1463116aa31c131131506597920000000014120033 to /home/exelsior/.compiz-1/session/105e8a1463116aa31c131131506597920000000014120033
[LOG]: Copied file /home/exelsior/.compiz/session/102efcea0ae8938118131402152132809200000014410033 to /home/exelsior/.compiz-1/session/102efcea0ae8938118131402152132809200000014410033
[LOG]: Copied file /home/exelsior/.compiz/session/107c00c222cb97c135131137387438280500000014400033 to /home/exelsior/.compiz-1/session/107c00c222cb97c135131137387438280500000014400033
[LOG]: Copied file /home/exelsior/.compiz/session/1053bf076b79855f9a131406642655434300000014360033 to /home/exelsior/.compiz-1/session/1053bf076b79855f9a131406642655434300000014360033
[LOG]: Copied file /home/exelsior/.compiz/session/1084a8da68c144addb131416423727391100000014910033 to /home/exelsior/.compiz-1/session/1084a8da68c144addb131416423727391100000014910033
[LOG]: Copied file /home/exelsior/.compiz/session/1084f90c43b70022a1131558745875455400000014480033 to /home/exelsior/.compiz-1/session/1084f90c43b70022a1131558745875455400000014480033
[LOG]: Copied file /home/exelsior/.compiz/session/10c060be175d45dbaf131503491319303200000014220033 to /home/exelsior/.compiz-1/session/10c060be175d45dbaf131503491319303200000014220033
[LOG]: Copied file /home/exelsior/.compiz/session/10aaff50bae8931921131662944721330100000014740033 to /home/exelsior/.compiz-1/session/10aaff50bae8931921131662944721330100000014740033
[LOG]: Copied file /home/exelsior/.compiz/session/10efea17916c8abb9d131441362856193700000014190033 to /home/exelsior/.compiz-1/session/10efea17916c8abb9d131441362856193700000014190033
[LOG]: Copied file /home/exelsior/.compiz/session/10b3312ace4e783691131528756153351400000013900033 to /home/exelsior/.compiz-1/session/10b3312ace4e783691131528756153351400000013900033
[LOG]: Copied file /home/exelsior/.compiz/session/10a048fa672090de73131647508941190700000016510033 to /home/exelsior/.compiz-1/session/10a048fa672090de73131647508941190700000016510033
[LOG]: Copied file /home/exelsior/.compiz/session/10c23d091b991e971e131698934596984200000014120033 to /home/exelsior/.compiz-1/session/10c23d091b991e971e131698934596984200000014120033
[LOG]: Copied file /home/exelsior/.compiz/session/10cc77c73c3b480e9b131653592862112900000014390033 to /home/exelsior/.compiz-1/session/10cc77c73c3b480e9b131653592862112900000014390033
[LOG]: Copied file /home/exelsior/.compiz/session/104be43eb6d4756401131681349590784400000014800033 to /home/exelsior/.compiz-1/session/104be43eb6d4756401131681349590784400000014800033
[LOG]: Copied file /home/exelsior/.compiz/session/10b0092758161e860e13170689755408100000014220033 to /home/exelsior/.compiz-1/session/10b0092758161e860e13170689755408100000014220033
[LOG]: Copied file /home/exelsior/.compiz/session/10af7f1a26a28f1362131751071724888900000014690033 to /home/exelsior/.compiz-1/session/10af7f1a26a28f1362131751071724888900000014690033
[LOG]: Copied file /home/exelsior/.compiz/session/10488b53a93e1c3a2c131802790876114600000014240033 to /home/exelsior/.compiz-1/session/10488b53a93e1c3a2c131802790876114600000014240033
[LOG]: Copied file /home/exelsior/.compiz/session/10da301e5ad074142b13171915802549300000014800033 to /home/exelsior/.compiz-1/session/10da301e5ad074142b13171915802549300000014800033
[LOG]: Copied file /home/exelsior/.compiz/session/10d8068120a8412d22131724605264274100000014420033 to /home/exelsior/.compiz-1/session/10d8068120a8412d22131724605264274100000014420033
[LOG]: Copied file /home/exelsior/.compiz/session/10bb291b9f8de67e1a131896542316071800000014650033 to /home/exelsior/.compiz-1/session/10bb291b9f8de67e1a131896542316071800000014650033
[LOG]: Copied file /home/exelsior/.compiz/session/109ff6e3b088b31249131848364136750700000014310033 to /home/exelsior/.compiz-1/session/109ff6e3b088b31249131848364136750700000014310033
[LOG]: Copied file /home/exelsior/.compiz/session/10fae2705421423633131742442452255400000014230033 to /home/exelsior/.compiz-1/session/10fae2705421423633131742442452255400000014230033
[LOG]: Copied file /home/exelsior/.compiz/session/101bbbd714d05ed92b131759643119034600000014480033 to /home/exelsior/.compiz-1/session/101bbbd714d05ed92b131759643119034600000014480033
[LOG]: Copied file /home/exelsior/.compiz/session/10a50dbbbfb1339ab2131809930625806300000014730033 to /home/exelsior/.compiz-1/session/10a50dbbbfb1339ab2131809930625806300000014730033
[LOG]: Copied file /home/exelsior/.compiz/session/109fe34ac2558dc56e130388790723398200000016020029 to /home/exelsior/.compiz-1/session/109fe34ac2558dc56e130388790723398200000016020029
[LOG]: Copied file /home/exelsior/.compiz/session/1067814fea11bcba47131819819051939600000014380033 to /home/exelsior/.compiz-1/session/1067814fea11bcba47131819819051939600000014380033
[LOG]: Copied file /home/exelsior/.compiz/session/10f5bca6642e59eaab131830647987628000000014270033 to /home/exelsior/.compiz-1/session/10f5bca6642e59eaab131830647987628000000014270033
[LOG]: Copied file /home/exelsior/.compiz/session/1081a27b59b5f0b9c2131860715654722100000013980033 to /home/exelsior/.compiz-1/session/1081a27b59b5f0b9c2131860715654722100000013980033
[LOG]: Copied file /home/exelsior/.compiz/session/10fc3c82abe3bccfa3131862950781742800000014810033 to /home/exelsior/.compiz-1/session/10fc3c82abe3bccfa3131862950781742800000014810033
[LOG]: Copied file /home/exelsior/.compiz/session/103eb344bbcab2f6f813186484243932500000015130033 to /home/exelsior/.compiz-1/session/103eb344bbcab2f6f813186484243932500000015130033
[LOG]: Copied file /home/exelsior/.compiz/session/107f663fbc7d7fa910131869401960997300000014360033 to /home/exelsior/.compiz-1/session/107f663fbc7d7fa910131869401960997300000014360033
[LOG]: Copied file /home/exelsior/.compiz/session/105a3e3a9135f40f4f131872226941488300000014430033 to /home/exelsior/.compiz-1/session/105a3e3a9135f40f4f131872226941488300000014430033
[LOG]: Copied file /home/exelsior/.compiz/session/10b9d43c454fbcb0ff131879968741101600000014480033 to /home/exelsior/.compiz-1/session/10b9d43c454fbcb0ff131879968741101600000014480033
[LOG]: Copied file /home/exelsior/.compiz/session/10746e6689d82ebc5613188433033200100000015100033 to /home/exelsior/.compiz-1/session/10746e6689d82ebc5613188433033200100000015100033
[LOG]: Copied file /home/exelsior/.compiz/session/1091abee64e469c32130380642947251900000016570029 to /home/exelsior/.compiz-1/session/1091abee64e469c32130380642947251900000016570029
[LOG]: Successfully moved internal files
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Processing upgrade com.canonical.unity.unity.01.upgrade
profile: unity
number: 1
domain: com.canonical.unity
Initializing composite options...done
Initializing splash options...done
Initializing place options...done
Initializing ezoom options...done
Initializing water options...done
Initializing put options...done
Initializing gnomecompat options...done
Initializing shift options...done
Initializing expo options...done
Initializing imgjpeg options...done
Initializing core options...done
Initializing mousepoll options...done
Initializing ring options...done
Initializing neg options...done
Initializing gtkloader options...done
Initializing workarounds options...done
Initializing mag options...done
Initializing vpswitch options...done
Initializing unityshell options...done
Initializing resize options...done
Initializing kdecompat options...done
Initializing screenshot options...done
Initializing mblur options...done
Initializing grid options...done
Initializing wallpaper options...done
Initializing thumbnail options...done
Initializing text options...done
Initializing rotate options...done
Initializing wobbly options...done
Initializing gears options...done
Initializing firepaint options...done
Initializing showmouse options...done
Initializing unitymtgrabhandles options...done
Initializing addhelper options...done
Initializing fade options...done
Initializing scalefilter options...done
Initializing fadedesktop options...done
Initializing shelf options...done
Initializing showdesktop options...done
Initializing move options...done
Initializing commands options...done
Initializing wall options...done
Initializing bench options...done
Initializing opacify options...done
Initializing cube options...done
Initializing cubeaddon options...done
Initializing decor options...done
Initializing reflex options...done
Initializing imgsvg options...done
Initializing colorfilter options...done
Initializing maximumize options...done
Initializing staticswitcher options...done
Initializing animation options...done
Initializing animationaddon options...done
Initializing scale options...done
Initializing bicubic options...done
Initializing group options...done
Initializing annotate options...done
Initializing copytex options...done
Initializing blur options...done
Initializing regex options...done
Initializing widget options...done
Initializing session options...done
Initializing winrules options...done
Initializing crashhandler options...done
Initializing inotify options...done
Initializing imgpng options...done
Initializing extrawm options...done
Initializing loginout options...done
Initializing snap options...done
Initializing obs options...done
Initializing bailer options...done
Initializing dbus options...done
Initializing td options...done
Initializing switcher options...done
Initializing clone options...done
Initializing scaleaddon options...done
Initializing opengl options...done
Initializing trailfocus options...done
Initializing detection options...done
Initializing notification options...done
Initializing resizeinfo options...done
Initializing debugspew options...done
Initializing zoom options...done
Initializing compiztoolbox options...done
Removed 0 items from active_plugins
Overriding value alt_tab_timeout
Completed upgrade com.canonical.unity.unity.01.upgrade
Processing upgrade com.canonical.unity.unity.02.upgrade
profile: unity
number: 2
domain: com.canonical.unity
Overriding value x_offset
Overriding value y_offset
Overriding value distance
Overriding value vp_distance
Overriding value vp_brightness
Overriding value vp_saturation
Overriding value reflection
Completed upgrade com.canonical.unity.unity.02.upgrade
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libopengl.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'opengl'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libcompiztoolbox.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'compiztoolbox'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libdecor.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'decor'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libresize.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'resize'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libgrid.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'grid'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunitymtgrabhandles.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unitymtgrabhandles'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libmove.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'move'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libwall.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'wall'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libanimation.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'animation'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libexpo.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'expo'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libworkarounds.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'workarounds'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libfade.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'fade'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libscale.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'scale'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libezoom.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'ezoom'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunityshell.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unityshell'
Setting Update "autoraise"
Setting Update "autoraise_delay"
Setting Update "maximize_window_key"
Setting Update "minimize_window_key"
Setting Update "show_desktop_key"
Setting Update "toggle_window_maximized_key"
Setting Update "toggle_window_shaded_key"
Setting Update "main_menu_key"
Setting Update "run_command_terminal_key"
Setting Update "run_key"

```

Just stopped there.

---

### Post by collisionystm on 2011-10-19
Try

Sudo apt-get install unity

---

### Post by Godsrycht on 2011-10-19
Says I already have the latest version. Also if it helps I also cannot minimise or move windows at all, where they open is where they stay.

---

### Post by Godsrycht on 2011-10-19
Tried --reset once more for shnitz n gigs and got 

```

"unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libopengl.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'opengl'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libdecor.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'decor'
Initializing mousepoll options...done
Initializing vpswitch options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libanimation.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'animation'
Initializing snap options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libexpo.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'expo'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libmove.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'move'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libcompiztoolbox.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'compiztoolbox'
Initializing place options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libgrid.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'grid'
Initializing gnomecompat options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libwall.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'wall'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libezoom.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'ezoom'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libworkarounds.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'workarounds'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libresize.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'resize'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libfade.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'fade'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunitymtgrabhandles.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unitymtgrabhandles'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libscale.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'scale'
Initializing session options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunityshell.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unityshell'
Initializing addhelper options...done
Initializing animation options...done
Initializing animationaddon options...done
Initializing annotate options...done
Initializing bench options...done
Initializing blur options...done
Initializing clone options...done
Initializing colorfilter options...done
Initializing commands options...done
Initializing resize options...done
Initializing move options...done
Initializing crashhandler options...done
Initializing cube options...done
Initializing cubeaddon options...done
Initializing debugspew options...done
Initializing decor options...done
Initializing expo options...done
Initializing extrawm options...done
Initializing ezoom options...done
Initializing fade options...done
Initializing fadedesktop options...done
Initializing firepaint options...done
Initializing grid options...done
Initializing group options...done
Initializing imgjpeg options...done
Initializing kdecompat options...done
Initializing loginout options...done
Initializing mag options...done
Initializing maximumize options...done
Initializing mblur options...done
Initializing neg options...done
Initializing notification options...done
Initializing obs options...done
Initializing opacify options...done
Initializing opengl options...done
Initializing put options...done
Initializing reflex options...done
Initializing resizeinfo options...done
Initializing ring options...done
Initializing rotate options...done
Initializing scale options...done
Initializing scaleaddon options...done
Initializing scalefilter options...done
Initializing screenshot options...done
Initializing shelf options...done
Initializing shift options...done
Initializing showdesktop options...done
Initializing showmouse options...done
Initializing splash options...done
Initializing staticswitcher options...done
Initializing switcher options...done
Initializing td options...done
Initializing thumbnail options...done
Initializing trailfocus options...done
Initializing unitymtgrabhandles options...done
Initializing unityshell options...done
Initializing wall options...done
Initializing wallpaper options...done
Initializing water options...done
Initializing widget options...done
Initializing winrules options...done
Initializing wobbly options...done
Initializing workarounds options...done
Initializing zoom options...done
Setting Update "main_menu_key"
Setting Update "run_key"
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2600003
"

```
This run_key thing seems to be what's screwin' my pooch.

---

### Post by collisionystm on 2011-10-19
Sudo apt-get install unity --reinstall

---

### Post by Godsrycht on 2011-10-19
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgladeui-1-11 libgnome-desktop-2-17
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/893 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 216807 files and directories currently installed.)
Preparing to replace unity 4.22.0-0ubuntu3 (using .../unity_4.22.0-0ubuntu3_i386.deb) ...
Unpacking replacement unity ...
Processing triggers for man-db ...
Setting up unity (4.22.0-0ubuntu3) ...

```

Am I winning yet?

---

### Post by collisionystm on 2011-10-19
I hope. Log out and back in when done

---

### Post by ARooster on 2011-10-19
hopefully so. I'd say the problem is with the OpenGL library...

---

### Post by Godsrycht on 2011-10-19
Reset the PC... still nothin' wanna lend me a gun with one bullet?

The good new however is after the restart I regained control of the 'minimize' 'fullscreen' and 'exit' bubbles and I can now move things around on my desktop.

---

### Post by ARooster on 2011-10-19
Hey, what is your GPU?

---

### Post by collisionystm on 2011-10-19
Lol sure. How about 2 in case the first doesn't do the trick

---

### Post by ARooster on 2011-10-19
??? But having two guns and only one bullet is kind of pointless, isn't it?

Seriously though, Godsrycht, what's your graphics card?

---

### Post by collisionystm on 2011-10-19
Install gnome so you at least have something to use

Sudo apt-get install gnome 

Log out choose gnome as your session

---

### Post by Godsrycht on 2011-10-19
> **ARooster said:**
> Hey, what is your GPU?
HD 56xx mobile, is there something in that info that would help? And no I'm a good shot, the second bullet would encourage me to take the punk teenage kid down stairs with me.

---

### Post by collisionystm on 2011-10-19
Install fglrx

---

### Post by collisionystm on 2011-10-19
> **Godsrycht said:**
> HD 56xx mobile, is there something in that info that would help? And no I'm a good shot, the second bullet would encourage me to take the punk teenage kid down stairs with me.

Hahaha

---

### Post by Godsrycht on 2011-10-19
What is metacity? Can I just use that? I don't know anything about Unity and in that ignorance would gladly sacrifice it for something a bit more... not broken.

---

### Post by Godsrycht on 2011-10-19
OK fglrx install just fine but no immediate changes were made should I restart?

---

### Post by collisionystm on 2011-10-19
Yes

---

### Post by Godsrycht on 2011-10-19
OK so no advancement on the GUI issue but I couldnt help but notice upon installing your gfxlr or whatever thing my PC now plays the catchy african start up mating call so Im assuming it gave me sound.

---

### Post by collisionystm on 2011-10-19
Sweet! 

Did you try to install gnome?

---

### Post by Godsrycht on 2011-10-19
Doing that now, Kind of sad though, upgrade to 11.10 then go right back to 11.04. Bummer.

---

### Post by ARooster on 2011-10-19
did you also try to go into your user account in Unity 2D? Does that work?

---

### Post by Godsrycht on 2011-10-19
No I haven't tried that yet. Think it would make a diff??

---

### Post by ARooster on 2011-10-19
Well if you can manage a back-up, format and a fresh install, that fixed quite a few problems for me. I had lots of problems (although not as severe and quite different) with the update from 11.04 to 11.10, the clean install is working much better (which shouldn't really be a surprise as that's the recommended way to go about updating anyway).

---

### Post by ARooster on 2011-10-19
well it would at least give you a workable desktop while you try and find the glitch.

---

### Post by Godsrycht on 2011-10-19
Is there a hot key list for logging out? I just keep hard resetting my PC>..

---

### Post by ubudog on 2011-10-19
Please be sure to add code brackets around console output, and code.

---

### Post by Godsrycht on 2011-10-19
> **ubudog said:**
> Please be sure to add code brackets around console output, and code.
Roger that. Sorry boss.

---

### Post by ubudog on 2011-10-19
> **Godsrycht said:**
> Roger that. Sorry boss.

:P No problem.

---

### Post by ARooster on 2011-10-19
To reboot enter following into the console window:

---

### Post by ARooster on 2011-10-19
```
sudo reboot
```

---

### Post by Godsrycht on 2011-10-19
OK, so I selected the cogwheel next to my log in and went to 'Ubuntu 2D' which seems to work just fine. I have all my stuff back. I'm gonna just stick with it. Thanks for all the help guys.

---

### Post by ubudog on 2011-10-19
> **Godsrycht said:**
> OK, so I selected the cogwheel next to my log in and went to 'Ubuntu 2D' which seems to work just fine. I have all my stuff back. I'm gonna just stick with it. Thanks for all the help guys.

Great, enjoy Ubuntu.

---

### Post by ARooster on 2011-10-19
Oh I see! Well in that case I'd suggest you get the ATI driver for your graphics card. I'd say that's the most likely culprit for the 3D mode not working.

And as ubudog said, enjoy Ubuntu :)

---

### Post by Godsrycht on 2011-10-19
> **ARooster said:**
> Oh I see! Well in that case I'd suggest you get the ATI driver for your graphics card. I'd say that's the most likely culprit for the 3D mode not working.

And as ubudog said, enjoy Ubuntu :)

I keep trying that but when I try to run the .run file ubuntu software center says I'm lying and the file isn't real.

---

### Post by ubudog on 2011-10-20
Try running it like so:
```
chmod +x file.run
```
```
./file.run
```

Assuming the file is in your home directory.

---

