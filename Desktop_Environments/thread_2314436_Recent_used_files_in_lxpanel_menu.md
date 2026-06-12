---
title: "Recent used files in lxpanel menu"
date: 2016-02-21
forum: Desktop Environments
---

### Post by haitem-belgacem on 2016-02-21
Hello,
i searched on the net if an application who show last used files in Lubuntu exist, but i haven't found.
so i've decided to develop a script.

it is compatible with : zip manager file-roller, gedit, acrobat 9, abiword, gnumeric, libreoffice suite, pdf viewer evince, darktable, gimp, inkscape, geany, audacious, audacity, gnome mplayer, vlc, openshot and google chrome.

the code is a simple installer. copy the code on text document and save .sh
he can desinstall too


if you have remarks, add or find bug, Do not hesitate to write to me

thank you

```
#!/bin/bash


#################################################################################
# Début de la fonction qui modifie le menu LXDE pour ajouter la partie Historique
#################################################################################
	function creer_menu
	{
####### Début de la sauvegarde ##################################################
		if [ ! -f /etc/xdg/lubuntu/menus/lxde-applications.menu.old ]
		then
			cp /etc/xdg/lubuntu/menus/lxde-applications.menu /etc/xdg/lubuntu/menus/lxde-applications.menu.old
		fi
####### Fin de la sauvegarde ####################################################


####### Début de l'ajout du menu Historique et des préférences ##################
		awk '/-- Applications Menu --/ { print; print "	<Menu>\n\
		<Name>Historique</Name>\n\
		<Directory>historique.directory</Directory>\n\
		<Include>\n\
			<And>\n\
				<Category>Historique</Category>\n\
			</And>\n\
		</Include>\n\
	</Menu>\n\
	<Menu>\n\
		<Name>PreferencesHistorique</Name>\n\
		<Directory>preferences-historique.directory</Directory>\n\
		<Include>\n\
			<And>\n\
				<Category>PreferencesHistorique</Category>\n\
			</And>\n\
		</Include>\n\
	</Menu>"; next }1' /etc/xdg/lubuntu/menus/lxde-applications.menu > /etc/xdg/lubuntu/menus/lxde-applications.menu2
		mv /etc/xdg/lubuntu/menus/lxde-applications.menu2 /etc/xdg/lubuntu/menus/lxde-applications.menu 
####### Fin de l'ajout du menu Historique et des préférences ####################


####### Début du placement des menus ############################################
		awk '/<Layout>/ { print; print "		<Menuname>Historique</Menuname>\n\
		<Menuname>PreferencesHistorique</Menuname>\n\
		<Separator/>"; next }1' /etc/xdg/lubuntu/menus/lxde-applications.menu > /etc/xdg/lubuntu/menus/lxde-applications.menu2
		mv /etc/xdg/lubuntu/menus/lxde-applications.menu2 /etc/xdg/lubuntu/menus/lxde-applications.menu
####### Fin du placement des menus ##############################################


####### Début de la création du sous-menu historique ############################
		echo "[Desktop Entry]
Name=Historique
Comment=Historique
Icon=document-open-recent
Type=Directory
X-Ubuntu-Gettext-Domain=gnome-menus-3.0" > /usr/share/desktop-directories/historique.directory
####### Fin de la création du sous-menu historique ##############################


####### Début de la création du sous-menu préférences de l'historique ###########
		echo "[Desktop Entry]
Name=Préférences historique
Comment=Préférences de l'historique
Icon=gnome-system
Type=Directory
X-Ubuntu-Gettext-Domain=gnome-menus-3.0" > /usr/share/desktop-directories/preferences-historique.directory
####### Fin de la création du sous-menu préférences de l'historique #############
	}
#################################################################################
# Fin de la fonction qui modifie le menu LXDE pour ajouter la partie Récents ####
#################################################################################


#############################################################################################
# Début de la fonction crée le script de configuration du nombre d'éléments dans l'historique
#############################################################################################
	function creer_conf
	{
####### Début de la création du script nombre d'éléments ####################################
		mkdir /opt/Recents
		echo "#!/bin/bash
if [ -f /home/\$USER/.nombre-elements.txt ]
then
	maxHistory=\$(tail /home/\$USER/.nombre-elements.txt)
else
	maxHistory=10
fi
nombre=\$(whiptail --title \"Nombre d'éléments dans l'historique\" --inputbox \"Combien d'éléments voulez-vous dans l'historique?\" 8 78 \$maxHistory 3>&1 1>&2 2>&3)


if [[ \$nombre < \$maxHistory ]]
then
	for ((i=\$maxHistory; i>\$nombre; i--))
		do
			rm /home/\$USER/.local/share/applications/\$i-history.desktop
		done
fi
echo \$nombre > /home/\$USER/.nombre-elements.txt" > /opt/Recents/nombre-elements.sh


####### Fin de la création du script nombre d'éléments ######################################


####### Début de la création du raccourci nombre d'éléments #################################
		echo "[Desktop Entry]
Encoding=UTF-8
Name=Nombre d'éléments
Comment=Indiquer le nombre d'éléments à afficher dans l'historique
Exec=lxterminal --command=\"bash /opt/Recents/nombre-elements.sh\"
Icon=gnome-system
Type=Application
Categories=PreferencesHistorique;" > /usr/share/applications/nombre-elements.desktop
####### Fin de la création du raccourci nombre d'éléments ###################################
	}
#############################################################################################
# Fin de la fonction crée le script de configuration du nombre d'éléments dans l'historique #
#############################################################################################


#####################################################################################
# Début de la fonction crée le script de purge du nombre d'éléments dans l'historique
#####################################################################################
	function creer_clear
	{
####### Début de la création du script clear ########################################
		echo "#!/bin/bash
rm /home/\$USER/.local/share/applications/*-history.desktop" > /opt/Recents/clear-history.sh
####### Fin de la création du script clear ##########################################


####### Début de la création du raccourci clear #####################################
		echo "[Desktop Entry]
Encoding=UTF-8
Name=Vider l'historique
Comment=Vide la liste des fichiers récents
Exec=lxterminal --command=\"bash /opt/Recents/clear-history.sh\"
Icon=edit-delete
Type=Application
Categories=PreferencesHistorique;" > /usr/share/applications/clear-history.desktop
####### Fin de la création du raccourci clear #######################################
	}
#####################################################################################
# Fin de la fonction crée le script de purge du nombre d'éléments dans l'historique #
#####################################################################################


#####################################################
# Début de la fonction crée le script de l'historique
#####################################################
	function creer_historique
	{
		echo "#!/bin/bash


#################################################
# Début de déclaration des variables essentielles
#################################################
	dateReference=\$(date +%s)
	maxHistory=\"10\"
	
	if [ ! -d /home/\$USER/.local/share/applications ]
	then
		mkdir /home/\$USER/.local/share/applications
	fi


	fileUsed=\"§\"
	fileName=\"§\"
#################################################
# Fin de déclaration des variables essentielles #
#################################################


#####################################################
# Début de la fonction de ré-encondage des caractères
#####################################################
	function reEncoding
	{
		fileUsed=\$(echo \$fileUsed | sed \"s/%20/ /g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%80/À/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%82/Â/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%84/Ä/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%88/È/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%89/É/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%8A/Ê/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%8B/Ë/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%8E/Î/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%8F/Ï/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%94/Ô/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%96/Ö/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%9B/Û/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%9C/Ü/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%A0/à/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%A2/â/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%A4/ä/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%A7/ç/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%A8/è/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%A9/é/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%AA/ê/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%AB/ë/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%AE/î/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%AF/ï/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%B4/ô/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%B6/ö/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%B9/ù/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%BB/û/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%BC/ü/g\")
	}
#####################################################
# Fin de la fonction de ré-encondage des caractères #
#####################################################


################################################
# Début de la fonction décalement des raccourcis
################################################
	function moveList
	{
		if [ -f /home/\$USER/.nombre-elements.txt ]
		then
			maxHistory=\$(tail /home/\$USER/.nombre-elements.txt)
		fi
		
		for ((i=\$maxHistory; i>1; i--))
		do
			j=\$((i-1))
			move=\$(mv /home/\$USER/.local/share/applications/\$j-history.desktop /home/\$USER/.local/share/applications/\$i-history.desktop)
		done
	}
################################################
# Fin de la fonction décalement des raccourcis #
################################################


#######################################################
# Début de la fonction d'écriture du raccourci numéro 1
#######################################################
	function createOne
	{
		if [ ! -f /home/\$USER/.local/share/applications/1-history.desktop ]
		then
			touch /home/\$USER/.local/share/applications/1-history.desktop
		fi
		
		echo \"[Desktop Entry]
Name=\$fileName
Comment=\$fileUsed
Exec=\$applicationUsed \\\"\$fileUsed\\\"
Icon=\$iconUsed
Type=Application
Categories=Historique;\" > /home/\$USER/.local/share/applications/1-history.desktop
	}
#######################################################
# Fin de la fonction d'écriture du raccourci numéro 1 #
#######################################################


#############################################################
# Début de la fonction de traitement de l'historique de geany
#############################################################
	function recentlyGeany
	{
		fileUsed=\$(tail /home/\$USER/.config/geany/geany.conf | grep \"recent_files=\")


########### Début d'isolation du fichier modifié ############
		fileUsed=\$(echo \"\${fileUsed%%;*}\") # On supprime la fin
		fileUsed=\$(echo \$fileUsed | sed -e \"s/recent_files=//\")
########### Fin d'isolation du fichier modifié ##############


		deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\")
		if [[ ! \$(echo \$deja | grep \"\$fileUsed\") ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
		then
			fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
			iconUsed=\"geany\"
			applicationUsed=\"geany %u\"
			moveList
			createOne
		fi
		changed=1
	}
#############################################################
# Fin de la fonction de traitement de l'historique de geany #
#############################################################


###############################################################
# Début de la fonction de traitement de l'historique de abiword
###############################################################
	function recentlyAbiword
	{
		fileUsed=\$(cat /home/\$USER/.config/abiword/profile | grep \"name1=\")
		if [[ ! \$(echo \$fileUsed | grep \"\$fileName\") ]]
		then
########### Début d'isolation du fichier modifié ##############
			fileUsed=\$(echo \$fileUsed | sed -e \"s/\\\"//g\")
			fileUsed=\$(echo \$fileUsed | sed -e \"s/name1=file:\/\///\")
########### Fin d'isolation du fichier modifié ################


			deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\")
			if [[ ! \$(echo \$deja | grep \"\$fileUsed\") ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
			then
				fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
				iconUsed=\"abiword\"
				applicationUsed=\"abiword %u\"
				moveList
				createOne
			fi
		fi
		changed=1
	}
###############################################################
# Fin de la fonction de traitement de l'historique de abiword #
###############################################################


###############################################################
# Début de la fonction de traitement de l'historique de acrobat
###############################################################
	function recentlyAcrobat
	{
		fileUsed=\$(cat -v /home/\$USER/.adobe/Acrobat/9.0/Preferences/reader_prefs | grep \"/RecentFiles\")
		if [[ ! \$(echo \$fileUsed | grep \"\$fileName\") ]]
		then
########### Début d'isolation du fichier modifié ##############
			fileUsed=\$(echo \$fileUsed | sed -e \"s/.*[(]//\") # on élimine le début
			fileUsed=\$(echo \$fileUsed | sed -e \"s/[)]\]//\") # on élimine la fin
########### Fin d'isolation du fichier modifié ################


			deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\")
			if [[ ! \$(echo \$deja | grep \"\$fileUsed\") ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
			then
				fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
				iconUsed=\"AdobeReader9\"
				applicationUsed=\"acroread\"
				moveList
				createOne
			fi
		fi
		changed=1
	}
###############################################################
# Fin de la fonction de traitement de l'historique de acrobat #
###############################################################


###################################################################
# Début de la fonction de traitement de l'historique de libreoffice
###################################################################
	function recentlyLibreoffice
	{
		fileUsed=\$(cat /home/\$USER/.config/libreoffice/4/user/registrymodifications.xcu | grep 'PickList' | grep 'oor:name=\"0\"')
		if [[ \$(echo \$fileUsed | grep \"file\") ]] # on vérifie si le grep retourne un champ vide
		then
			if [[ ! \$(echo \$fileUsed | grep \"\$fileName\") ]] # on évite le doublon en comparant avec l'entrée précédente
			then
############### Début d'isolation du fichier modifié ##############
				fileUsed=\$(echo \$fileUsed | sed -e \"s/.*file:\/\///\") # on élimine le début
				fileUsed=\$(echo \"\${fileUsed%%<*}\") # On supprime la fin
				reEncoding
############### Fin d'isolation du fichier modifié ################


				deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\")
				if [[ ! \$(echo \$deja | grep \"\$fileUsed\") ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
				then
					fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
					extension=\$(echo \$fileName | sed \"s/.*\.//\")


################### Début de définition des extensions ############
					if [[ \"\$extension\" = \"odt\" ]] || [[ \"\$extension\" = \"ott\" ]] || [[ \"\$extension\" = \"fodt\" ]] || [[ \"\$extension\" = \"uot\" ]] || [[ \"\$extension\" = \"doc\" ]] || [[ \"\$extension\" = \"docx\" ]] || [[ \"\$extension\" = \"dot\" ]] || [[ \"\$extension\" = \"rtf\" ]]
					then
						iconUsed=\"libreoffice-writer\"
						applicationUsed=\"libreoffice --writer %U\"
					elif [[ \"\$extension\" = \"odf\" ]] || [[ \"\$extension\" = \"mml\" ]]
					then
						iconUsed=\"libreoffice-math\"
						applicationUsed=\"libreoffice --math %U\"
					elif [[ \"\$extension\" = \"odp\" ]] || [[ \"\$extension\" = \"otp\" ]] || [[ \"\$extension\" = \"fodp\" ]] || [[ \"\$extension\" = \"uop\" ]] || [[ \"\$extension\" = \"ppt\" ]] || [[ \"\$extension\" = \"pptx\" ]] || [[ \"\$extension\" = \"ppsx\" ]] || [[ \"\$extension\" = \"potm\" ]] || [[ \"\$extension\" = \"pps\" ]] || [[ \"\$extension\" = \"pot\" ]]
					then
						iconUsed=\"libreoffice-impress\"
						applicationUsed=\"libreoffice --impress %U\"
					elif [[ \"\$extension\" = \"odg\" ]] || [[ \"\$extension\" = \"otg\" ]] || [[ \"\$extension\" = \"fodg\" ]]
					then
						iconUsed=\"libreoffice-draw\"
						applicationUsed=\"libreoffice --draw %U\"
					elif [[ \"\$extension\" = \"ods\" ]] || [[ \"\$extension\" = \"ots\" ]] || [[ \"\$extension\" = \"fods\" ]] || [[ \"\$extension\" = \"uos\" ]] || [[ \"\$extension\" = \"xlsx\" ]] || [[ \"\$extension\" = \"xls\" ]] || [[ \"\$extension\" = \"xlt\" ]] || [[ \"\$extension\" = \"csv\" ]]
					then
						iconUsed=\"libreoffice-calc\"
						applicationUsed=\"libreoffice --calc %U\"
					fi
################### Fin de définition des extensions ##############
					moveList
					createOne
				fi
			fi
		fi
		changed=1
	}
###################################################################
# Fin de la fonction de traitement de l'historique de libreoffice #
###################################################################


###############################################################
# Début de la fonction de traitement de l'historique de blender
###############################################################
	function recentlyBlender
	{
		fileUsed=\$(head -1 /home/\$USER/.config/blender/2.74/config/recent-files.txt)
		if [[ \$(echo \$fileUsed | grep \"/\") ]] # on vérifie si le grep retourne un champ vide
		then
			if [[ ! \$(echo \$fileUsed | grep \"\$fileName\") ]]
			then
				deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\")
				if [[ ! \$(echo \$deja | grep \"\$fileUsed\") ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
				then
					fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
					iconUsed=\"blender\"
					applicationUsed=\"blender %f\"
					moveList
					createOne
				fi
			fi
		fi
		changed=1
	}
###############################################################
# Fin de la fonction de traitement de l'historique de blender #
###############################################################


#################################################################
# Début de la fonction de traitement de l'historique de darktable
#################################################################
	function recentlyDarktable
	{
####### Début de récupération de la date de modification ########
		toGrep=\$(date --date=\"1970-01-01 \$dateDarktable sec GMT\" \"+%Y:%m:%d %H:%M:%S\")
		toGrep=\"\${toGrep:0:18}\"
####### Fin de récupération de la date de modification ##########


####### Début de la récupération des données à traiter ##########
		fileUsed=\$(cat -v /home/\$USER/.config/darktable/library.db | grep \"\$toGrep\" | sed -e \"s/\^@//g\")
####### Fin de la récupération des données à traiter ############


		if [[ \$fileUsed ]] # on vérifie si le grep retourne un champ vide
		then


########### Début d'extraction du chemin du fichier ouvert ######
			fileUsed=\$(echo \$fileUsed | sed -e \"s/\$toGrep/§/\")
			position=\`expr index \"\$fileUsed\" §\`
			fileUsed=\${fileUsed:(\$position+1)} # on élimine le début
			fileUsed=\$(echo \$fileUsed | sed -e \"s/:/§/\")
			fileUsed=\$(echo \"\${fileUsed%%§*}\") # On supprime la fin
			lastFolder=\$(echo \$fileUsed | sed \"s/.*\///\")
			lastFolder=\${lastFolder:0:3} # on elimine la fin
			fileUsed=\$(echo \"\${fileUsed%/*}\")
			fileUsed=\$(find \"\$fileUsed\" -maxdepth 1 -name \$lastFolder*)
########### Fin d'extraction du chemin du fichier ouvert ########


			if [[ \$(echo \$fileUsed | grep \" \/\") ]] # Si il existe plusieurs dossiers ayant les mêmes 3 premières lettres
			then
############### Début d'extraction du dossier parent ############
				fileUsed=\$(echo \$fileUsed | sed -e \"s/ \//§/\")
				fileUsed=\$(echo \"\${fileUsed%%§*}\") # On supprime la fin
				fileUsed2=\$(echo \"\${fileUsed%/*}\")
############### Fin d'extraction du dossier parent ##############
			else # sinon, il n'y a qu'un seul dossier avec le meme début de nom
				fileUsed=\$(find \"\$fileUsed\" -maxdepth 1 -name \"*.xmp\" -mmin -1)
				fileUsed=\$(echo \$fileUsed | sed -e \"s/ /%20/g\")
				fileUsed=\$(echo \$fileUsed | sed -e \"s/%20\// \//\")
				fileUsed2=\$(echo \$fileUsed)
			fi


			for fileUsed in \$fileUsed2 # Pour chaque éléments séparés par un espace
			do
############### Début de finalisation du traitement #############
				fileUsed=\$(echo \$fileUsed | sed -e \"s/§/ /g\")
				fileUsed=\$(echo \$fileUsed | sed -e \"s/.xmp//g\")
				reEncoding
############### Fin de finalisation du traitement ###############


				deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\")
				if [[ ! \$(echo \$deja | grep \"\$fileUsed\") ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
				then
################### Début de création du raccourci ##############
					fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
					iconUsed=\"darktable\"
					applicationUsed=\"darktable %U\"
					moveList
					createOne
################### Fin de création du raccourci ################
				fi
			done
		fi
		changed=1
	}
#################################################################
# Fin de la fonction de traitement de l'historique de darktable #
#################################################################


#################################################################
# Début de la fonction de traitement de l'historique de audacious
#################################################################
	function recentlyAudacious
	{
####### Début de la récupération des données à traiter ##########
		fileUsed=\$(cat /home/\$USER/.config/audacious/playlists/1000.audpl | grep \"uri=\")
####### Fin de la récupération des données à traiter ############


		if [[ \$(echo \$fileUsed | grep \"/\") ]] # on vérifie si le grep retourne un champ vide
		then


########### Début d'extraction du chemin du fichier ouvert ######
			fileUsed=\$(echo \$fileUsed | sed \"s/ uri=file:\/\//§/\")
			fileUsed=\$(echo \"\${fileUsed%%§*}\") # On supprime la fin
			fileUsed=\$(echo \$fileUsed | sed \"s/uri=file:\/\///\")
########### Fin d'extraction du chemin du fichier ouvert ########
			reEncoding


			if [[ ! \$(echo \$fileUsed | grep \"\$fileName\") ]]
			then


				deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\")
				if [[ ! \$(echo \$deja | grep \"\$fileUsed\") ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
				then
################### Début de création du raccourci ##############
					fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
					iconUsed=\"audacious\"
					applicationUsed=\"audacious %U\"
					moveList
					createOne
################### Fin de création du raccourci ################
				fi
			fi
		fi
		changed=1
	}
#################################################################
# Fin de la fonction de traitement de l'historique de audacious #
#################################################################


################################################################
# Début de la fonction de traitement de l'historique de audacity
################################################################
	function recentlyAudacity
	{
		if [[ \$(ps -e | grep audacity) ]]
		then
########### Début du la récupération du repère #################
			fileUsed=\$(tail -1 /home/\$USER/.audacity-data/audacity.cfg)
			toGrep=\$(echo \$fileUsed | sed -e \"s/.*=//\") # on supprime le début
			toGrep=\$(echo \$toGrep | sed -e \"s/\//\\\\\\\\\//g\")
########### Fin du la récupération du repère ###################


		else


############### Début d'extraction du chemin du fichier ouvert #
				fileUsed=\$(cat -v /home/\$USER/.audacity-data/audacity.cfg)
				fileUsed=\$(echo \$fileUsed | sed -e \"s/.*\$toGrep //\") # on élimine le début
				fileUsed2=\$(echo \$fileUsed | sed -e \"s/ /%20/g\")
				fileUsed2=\$(echo \$fileUsed2 | sed -e \"s/%20file/ file/g\")
############### Fin d'extraction du chemin du fichier ouvert ###


			for fileUsed in \$fileUsed2 # Pour chaque éléments séparés par un espace
			do
############### Début de finalisation du traitement #############
				fileUsed=\$(echo \$fileUsed | sed -e \"s/.*=//\")
				reEncoding
############### Fin de finalisation du traitement ###############


				deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\")
				if [[ ! \$(echo \$deja | grep \"\$fileUsed\") ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
				then
################### Début de création du raccourci ##############
					fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
					iconUsed=\"audacity\"
					applicationUsed=\"audacity %F\"
					moveList
					createOne
################### Fin de création du raccourci ################
				fi
			done
		fi
		changed=1
	}
################################################################
# Fin de la fonction de traitement de l'historique de audacity #
################################################################


###########################################################
# Début de la fonction de traitement de l'historique de vlc
###########################################################
	function recentlyVlc
	{
####### Début de la récupération des données à traiter ####
		fileUsed=\$(cat -v /home/\$USER/.config/vlc/vlc-qt-interface.conf | grep \"list=file\")
####### Fin de la récupération des données à traiter ######


		if [[ \$(echo \$fileUsed | grep \"/\") ]] # on vérifie si le grep retourne un champ vide
		then


########### Début d'extraction du chemin du fichier ouvert
			fileUsed=\$(echo \$fileUsed | sed \"s/list=file:\/\///\")
			fileUsed=\$(echo \$fileUsed | sed \"s/,/§/\")
			fileUsed=\$(echo \"\${fileUsed%§*}\") # On supprime la fin
########### Fin d'extraction du chemin du fichier ouvert ##
			reEncoding
			
			if [[ ! \$(echo \$fileUsed | grep \"\$fileName\") ]]
			then
				deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\")
				if [[ ! \$(echo \$deja | grep \"\$fileUsed\") ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
				then


################### Début de création du raccourci ########
					fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
					iconUsed=\"vlc\"
					applicationUsed=\"/usr/bin/vlc --started-from-file %U\"
					moveList
					createOne
################### Fin de création du raccourci ##########
				fi
			fi
		fi
		changed=1
	}
###########################################################
# Fin de la fonction de traitement de l'historique de vlc #
###########################################################


############################################################
# Début de la fonction de traitement de l'historique général
############################################################
	function recentlyUsedXbel
	{
####### Début d'extraction de la dernière entrée ###########
		toGrep=\$(date --date=\"1970-01-01 \$dateGeneralHistory sec\" +%Y-%m-%dT%H:%M:%S)
		toTreat=\$(cat /home/\$USER/.local/share/recently-used.xbel | grep \$toGrep)
####### Fin d'extraction de la dernière entrée #############


		if [[ \"\$toTreat\" = *\"bookmark\"* ]]
		then
			if [[ ! \$(echo \$toTreat | grep \"\$fileUsed\") ]] && [[ ! \$(echo \$toTreat | grep \"soffice\") ]] && [[ ! \$(echo \$toTreat | grep \"audacity\") ]]  && [[ ! \$(echo \$toTreat | grep \"darktable\") ]] # Si on retrouve le contenu de fileUsed dans toTreat, cela signifie que l'entrée précédente est la meme. on évite le doublon && si fileUsed contient soffice, ne pas s'executer && si fileUsed contient audacity, ne pas s'executer && si fileUsed contient darktable, ne pas s'executer
			then
############### Début d'isolation du fichier modifié #######
				fileUsed=\$(echo \$toTreat | sed -e \"s/.*file:\/\///\") # on supprime le début
				fileUsed=\$(echo \"\${fileUsed%%\\\"*}\") # On supprime la fin
				reEncoding # remplacement des codes caractères spéciaux du chemin vers le fichier
				if [ ! -f \"\$fileUsed\" ]
				then
					fileUsed=\$(ls \$fileUsed.*)
				fi
############### Fin d'isolation du fichier modifié #########


				deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\")
				if [[ ! \$(echo \$deja | grep \"\$fileUsed\") ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
				then


################### Début d'extraction de la date modified #
					toTreat=\$(echo \$toTreat | sed -e \"s/.*modified=\\\"//\") # on supprime le début
					toTreat=\$(echo \"\${toTreat%%Z*}\") # On supprime la fin
					toTreat=\$(cat /home/\$USER/.local/share/recently-used.xbel | grep \$toTreat)
################### Fin d'extraction de la date modified ###


################### Début d'isolation de l'application utilisé
					applicationUsed=\$(echo \$toTreat | sed -e \"s/.*exec=\\\"&apos;//\") # on supprime le début
					applicationUsed=\$(echo \"\${applicationUsed%%&*}\") # On supprime la fin
################### Fin d'isolation de l'application utilisé


					if [[ \"\$applicationUsed\" = *\"gedit\"* ]]
					then
						iconUsed=\"accessories-text-editor\"
					else
						iconUsed=\$(echo \$applicationUsed | sed -e \"s/ %u//\")
					fi


					fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
					moveList
					createOne
				fi
			fi
		fi
		changed=1
	}
############################################################
# Fin de la fonction de traitement de l'historique général #
############################################################


#########################
# Début du script général
#########################
	while true
	do
		changed=0
		dateGeneralHistory=\$(stat -c %Y /home/\$USER/.local/share/recently-used.xbel)
		dateGeany=\$(stat -c %Y /home/\$USER/.config/geany/geany.conf)
		dateAbiword=\$(stat -c %Y /home/\$USER/.config/abiword/profile)
		dateAcrobat=\$(stat -c %Y /home/\$USER/.adobe/Acrobat/9.0/Preferences/reader_prefs)
		dateLibreoffice=\$(stat -c %Y /home/\$USER/.config/libreoffice/4/user/registrymodifications.xcu)
		if [[ -f /home/\$USER/.config/blender/2.74/config/recent-files.txt ]]
		then
			dateBlender=\$(stat -c %Y /home/\$USER/.config/blender/2.74/config/recent-files.txt)
		fi
		dateDarktable=\$(stat -c %Y /home/\$USER/.config/darktable/library.db)
		dateAudacious=\$(stat -c %Y /home/\$USER/.config/audacious/playlists/1000.audpl)
		dateAudacity=\$(stat -c %Y /home/\$USER/.audacity-data/audacity.cfg)
		dateVlc=\$(stat -c %Y /home/\$USER/.config/vlc/vlc-qt-interface.conf)


		if [[ \"\$dateGeany\" > \"\$dateReference\" ]]
		then
			recentlyGeany
		fi


		if [[ \"\$dateAbiword\" > \"\$dateReference\" ]]
		then
			recentlyAbiword
		fi


		if [[ \"\$dateAcrobat\" > \"\$dateReference\" ]]
		then
			recentlyAcrobat
		fi


		if [[ \"\$dateLibreoffice\" > \"\$dateReference\" ]]
		then
			recentlyLibreoffice
		fi


		if [[ \"\$dateBlender\" > \"\$dateReference\" ]]
		then
			recentlyBlender
		fi


		if [[ \"\$dateDarktable\" > \"\$dateReference\" ]]
		then
			recentlyDarktable
		fi


		if [[ \"\$dateAudacious\" > \"\$dateReference\" ]]
		then
			recentlyAudacious
		fi


		if [[ \"\$dateAudacity\" > \"\$dateReference\" ]]
		then
			recentlyAudacity
		fi


		if [[ \"\$dateVlc\" > \"\$dateReference\" ]]
		then
			recentlyVlc
		fi


		if [[ \"\$dateGeneralHistory\" > \"\$dateReference\" ]]
		then
			recentlyUsedXbel
		fi


		if [[ \$changed == 1 ]]
		then
			dateReference=\$(date +%s)
		fi
		sleep 1
	done
#########################
# Fin du script général #
#########################" > /opt/Recents/historique.sh


		echo "[Desktop Entry]
Name=Script historique
Comment=Script historique
Exec=bash /opt/Recents/historique.sh" > /etc/xdg/autostart/historique.desktop
	}
#####################################################
# Fin de la fonction crée le script de l'historique #
#####################################################


###################################
# Début d'execution du code général
###################################
	temp=$(whoami)
	if [[ "$temp" != "root" ]]
	then
		whiptail --title "sudoer" --msgbox "Le programme doit être exécuté avec les droits super-administrateur sudo" 8 78
	else
		if [ -f /usr/share/desktop-directories/historique.directory ]
		then
			whiptail --title "Supprimer?" --yesno "Voulez-vous supprimer l'historique du menu?" --yes-button "Oui" --no-button "Non" 8 78 3>&1 1>&2 2>&3
			if [[ "$?" == "0" ]]
			then
				cp /etc/xdg/lubuntu/menus/lxde-applications.menu.old /etc/xdg/lubuntu/menus/lxde-applications.menu
				rm /usr/share/desktop-directories/historique.directory
				rm /usr/share/desktop-directories/preferences-historique.directory
				rm -rf /opt/Recents/
				rm /usr/share/applications/nombre-elements.desktop
				rm /usr/share/applications/clear-history.desktop
				rm /etc/xdg/autostart/historique.desktop
			fi
		else
			creer_menu
			creer_conf
			creer_clear
			creer_historique
		fi
	fi
#################################
# Fin d'execution du code général
#################################
```

---

### Post by haitem-belgacem on 2016-02-24
bug correction

```
#!/bin/bash

#################################################################################
# Début de la fonction qui modifie le menu LXDE pour ajouter la partie Historique
#################################################################################
    function creer_menu
    {
####### Début de la sauvegarde ##################################################
        if [ ! -f /etc/xdg/lubuntu/menus/lxde-applications.menu.old ]
        then
            cp /etc/xdg/lubuntu/menus/lxde-applications.menu /etc/xdg/lubuntu/menus/lxde-applications.menu.old
        fi
####### Fin de la sauvegarde ####################################################


####### Début de l'ajout du menu Historique et des préférences ##################
        awk '/-- Applications Menu --/ { print; print "    <Menu>\n\
        <Name>Historique</Name>\n\
        <Directory>historique.directory</Directory>\n\
        <Include>\n\
            <And>\n\
                <Category>Historique</Category>\n\
            </And>\n\
        </Include>\n\
    </Menu>\n\
    <Menu>\n\
        <Name>PreferencesHistorique</Name>\n\
        <Directory>preferences-historique.directory</Directory>\n\
        <Include>\n\
            <And>\n\
                <Category>PreferencesHistorique</Category>\n\
            </And>\n\
        </Include>\n\
    </Menu>"; next }1' /etc/xdg/lubuntu/menus/lxde-applications.menu > /etc/xdg/lubuntu/menus/lxde-applications.menu2
        mv /etc/xdg/lubuntu/menus/lxde-applications.menu2 /etc/xdg/lubuntu/menus/lxde-applications.menu 
####### Fin de l'ajout du menu Historique et des préférences ####################


####### Début du placement des menus ############################################
        awk '/<Layout>/ { print; print "        <Menuname>Historique</Menuname>\n\
        <Menuname>PreferencesHistorique</Menuname>\n\
        <Separator/>"; next }1' /etc/xdg/lubuntu/menus/lxde-applications.menu > /etc/xdg/lubuntu/menus/lxde-applications.menu2
        mv /etc/xdg/lubuntu/menus/lxde-applications.menu2 /etc/xdg/lubuntu/menus/lxde-applications.menu
####### Fin du placement des menus ##############################################


####### Début de la création du sous-menu historique ############################
        echo "[Desktop Entry]
Name=Historique
Comment=Historique
Icon=document-open-recent
Type=Directory
X-Ubuntu-Gettext-Domain=gnome-menus-3.0" > /usr/share/desktop-directories/historique.directory
####### Fin de la création du sous-menu historique ##############################


####### Début de la création du sous-menu préférences de l'historique ###########
        echo "[Desktop Entry]
Name=Préférences historique
Comment=Préférences de l'historique
Icon=gnome-system
Type=Directory
X-Ubuntu-Gettext-Domain=gnome-menus-3.0" > /usr/share/desktop-directories/preferences-historique.directory
####### Fin de la création du sous-menu préférences de l'historique #############
    }
#################################################################################
# Fin de la fonction qui modifie le menu LXDE pour ajouter la partie Récents ####
#################################################################################


#############################################################################################
# Début de la fonction crée le script de configuration du nombre d'éléments dans l'historique
#############################################################################################
    function creer_conf
    {
####### Début de la création du script nombre d'éléments ####################################
        mkdir /opt/Recents
        echo "#!/bin/bash
if [ -f /home/\$USER/.nombre-elements.txt ]
then
    maxHistory=\$(tail /home/\$USER/.nombre-elements.txt)
else
    maxHistory=10
fi
nombre=\$(whiptail --title \"Nombre d'éléments dans l'historique\" --inputbox \"Combien d'éléments voulez-vous dans l'historique?\" 8 78 \$maxHistory 3>&1 1>&2 2>&3)


if [[ \$nombre < \$maxHistory ]]
then
    for ((i=\$maxHistory; i>\$nombre; i--))
        do
            rm /home/\$USER/.local/share/applications/\$i-history.desktop
        done
fi
echo \$nombre > /home/\$USER/.nombre-elements.txt" > /opt/Recents/nombre-elements.sh


####### Fin de la création du script nombre d'éléments ######################################


####### Début de la création du raccourci nombre d'éléments #################################
        echo "[Desktop Entry]
Encoding=UTF-8
Name=Nombre d'éléments
Comment=Indiquer le nombre d'éléments à afficher dans l'historique
Exec=lxterminal --command=\"bash /opt/Recents/nombre-elements.sh\"
Icon=gnome-system
Type=Application
Categories=PreferencesHistorique;" > /usr/share/applications/nombre-elements.desktop
####### Fin de la création du raccourci nombre d'éléments ###################################
    }
#############################################################################################
# Fin de la fonction crée le script de configuration du nombre d'éléments dans l'historique #
#############################################################################################


#####################################################################################
# Début de la fonction crée le script de purge du nombre d'éléments dans l'historique
#####################################################################################
    function creer_clear
    {
####### Début de la création du script clear ########################################
        echo "#!/bin/bash
rm /home/\$USER/.local/share/applications/*-history.desktop" > /opt/Recents/clear-history.sh
####### Fin de la création du script clear ##########################################


####### Début de la création du raccourci clear #####################################
        echo "[Desktop Entry]
Encoding=UTF-8
Name=Vider l'historique
Comment=Vide la liste des fichiers récents
Exec=lxterminal --command=\"bash /opt/Recents/clear-history.sh\"
Icon=edit-delete
Type=Application
Categories=PreferencesHistorique;" > /usr/share/applications/clear-history.desktop
####### Fin de la création du raccourci clear #######################################
    }
#####################################################################################
# Fin de la fonction crée le script de purge du nombre d'éléments dans l'historique #
#####################################################################################


#####################################################
# Début de la fonction crée le script de l'historique
#####################################################
    function creer_historique
    {
        echo "#!/bin/bash


#################################################
# Début de déclaration des variables essentielles
#################################################
    dateReference=\$(date +%s)
    maxHistory=\"10\"
    
    if [ ! -d /home/\$USER/.local/share/applications ]
    then
        mkdir /home/\$USER/.local/share/applications
    fi


    fileUsed=\"§\"
    fileName=\"§\"
#################################################
# Fin de déclaration des variables essentielles #
#################################################


#####################################################
# Début de la fonction de ré-encondage des caractères
#####################################################
    function reEncoding
    {
        fileUsed=\$(echo \$fileUsed | sed \"s/%20/ /g\")
        fileUsed=\$(echo \$fileUsed | sed \"s/%C3%80/À/g\")
        fileUsed=\$(echo \$fileUsed | sed \"s/%C3%82/Â/g\")
        fileUsed=\$(echo \$fileUsed | sed \"s/%C3%84/Ä/g\")
        fileUsed=\$(echo \$fileUsed | sed \"s/%C3%88/È/g\")
        fileUsed=\$(echo \$fileUsed | sed \"s/%C3%89/É/g\")
        fileUsed=\$(echo \$fileUsed | sed \"s/%C3%8A/Ê/g\")
        fileUsed=\$(echo \$fileUsed | sed \"s/%C3%8B/Ë/g\")
        fileUsed=\$(echo \$fileUsed | sed \"s/%C3%8E/Î/g\")
        fileUsed=\$(echo \$fileUsed | sed \"s/%C3%8F/Ï/g\")
        fileUsed=\$(echo \$fileUsed | sed \"s/%C3%94/Ô/g\")
        fileUsed=\$(echo \$fileUsed | sed \"s/%C3%96/Ö/g\")
        fileUsed=\$(echo \$fileUsed | sed \"s/%C3%9B/Û/g\")
        fileUsed=\$(echo \$fileUsed | sed \"s/%C3%9C/Ü/g\")
        fileUsed=\$(echo \$fileUsed | sed \"s/%C3%A0/à/g\")
        fileUsed=\$(echo \$fileUsed | sed \"s/%C3%A2/â/g\")
        fileUsed=\$(echo \$fileUsed | sed \"s/%C3%A4/ä/g\")
        fileUsed=\$(echo \$fileUsed | sed \"s/%C3%A7/ç/g\")
        fileUsed=\$(echo \$fileUsed | sed \"s/%C3%A8/è/g\")
        fileUsed=\$(echo \$fileUsed | sed \"s/%C3%A9/é/g\")
        fileUsed=\$(echo \$fileUsed | sed \"s/%C3%AA/ê/g\")
        fileUsed=\$(echo \$fileUsed | sed \"s/%C3%AB/ë/g\")
        fileUsed=\$(echo \$fileUsed | sed \"s/%C3%AE/î/g\")
        fileUsed=\$(echo \$fileUsed | sed \"s/%C3%AF/ï/g\")
        fileUsed=\$(echo \$fileUsed | sed \"s/%C3%B4/ô/g\")
        fileUsed=\$(echo \$fileUsed | sed \"s/%C3%B6/ö/g\")
        fileUsed=\$(echo \$fileUsed | sed \"s/%C3%B9/ù/g\")
        fileUsed=\$(echo \$fileUsed | sed \"s/%C3%BB/û/g\")
        fileUsed=\$(echo \$fileUsed | sed \"s/%C3%BC/ü/g\")
    }
#####################################################
# Fin de la fonction de ré-encondage des caractères #
#####################################################


################################################
# Début de la fonction décalement des raccourcis
################################################
    function moveList
    {
        if [ -f /home/\$USER/.nombre-elements.txt ]
        then
            maxHistory=\$(tail /home/\$USER/.nombre-elements.txt)
        fi
        
        for ((i=\$maxHistory; i>1; i--))
        do
            j=\$((i-1))
            move=\$(mv /home/\$USER/.local/share/applications/\$j-history.desktop /home/\$USER/.local/share/applications/\$i-history.desktop)
        done
    }
################################################
# Fin de la fonction décalement des raccourcis #
################################################


#######################################################
# Début de la fonction d'écriture du raccourci numéro 1
#######################################################
    function createOne
    {
        if [ ! -f /home/\$USER/.local/share/applications/1-history.desktop ]
        then
            touch /home/\$USER/.local/share/applications/1-history.desktop
        fi
        
        echo \"[Desktop Entry]
Name=\$fileName
Comment=\$fileUsed
Exec=\$applicationUsed \\\"\$fileUsed\\\"
Icon=\$iconUsed
Type=Application
Categories=Historique;\" > /home/\$USER/.local/share/applications/1-history.desktop
    }
#######################################################
# Fin de la fonction d'écriture du raccourci numéro 1 #
#######################################################


#############################################################
# Début de la fonction de traitement de l'historique de geany
#############################################################
    function recentlyGeany
    {
        fileUsed=\$(tail /home/\$USER/.config/geany/geany.conf | grep \"recent_files=\")


########### Début d'isolation du fichier modifié ############
        fileUsed=\$(echo \"\${fileUsed%%;*}\") # On supprime la fin
        fileUsed=\$(echo \$fileUsed | sed -e \"s/recent_files=//\")
########### Fin d'isolation du fichier modifié ##############


        deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\")
        if [[ ! \$(echo \$deja | grep \"\$fileUsed\") ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
        then
            fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
            iconUsed=\"geany\"
            applicationUsed=\"geany %u\"
            moveList
            createOne
        fi
        changed=1
    }
#############################################################
# Fin de la fonction de traitement de l'historique de geany #
#############################################################


###############################################################
# Début de la fonction de traitement de l'historique de abiword
###############################################################
    function recentlyAbiword
    {
        fileUsed=\$(cat /home/\$USER/.config/abiword/profile | grep \"name1=\")
        if [[ ! \$(echo \$fileUsed | grep \"\$fileName\") ]]
        then
########### Début d'isolation du fichier modifié ##############
            fileUsed=\$(echo \$fileUsed | sed -e \"s/\\\"//g\")
            fileUsed=\$(echo \$fileUsed | sed -e \"s/name1=file:\/\///\")
########### Fin d'isolation du fichier modifié ################


            deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\")
            if [[ ! \$(echo \$deja | grep \"\$fileUsed\") ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
            then
                fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
                iconUsed=\"abiword\"
                applicationUsed=\"abiword %u\"
                moveList
                createOne
            fi
        fi
        changed=1
    }
###############################################################
# Fin de la fonction de traitement de l'historique de abiword #
###############################################################


###############################################################
# Début de la fonction de traitement de l'historique de acrobat
###############################################################
    function recentlyAcrobat
    {
        fileUsed=\$(cat -v /home/\$USER/.adobe/Acrobat/9.0/Preferences/reader_prefs | grep \"/RecentFiles\")
        if [[ ! \$(echo \$fileUsed | grep \"\$fileName\") ]]
        then
########### Début d'isolation du fichier modifié ##############
            fileUsed=\$(echo \$fileUsed | sed -e \"s/.*[(]//\") # on élimine le début
            fileUsed=\$(echo \$fileUsed | sed -e \"s/[)]\]//\") # on élimine la fin
########### Fin d'isolation du fichier modifié ################


            deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\")
            if [[ ! \$(echo \$deja | grep \"\$fileUsed\") ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
            then
                fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
                iconUsed=\"AdobeReader9\"
                applicationUsed=\"acroread\"
                moveList
                createOne
            fi
        fi
        changed=1
    }
###############################################################
# Fin de la fonction de traitement de l'historique de acrobat #
###############################################################


###################################################################
# Début de la fonction de traitement de l'historique de libreoffice
###################################################################
    function recentlyLibreoffice
    {
        fileUsed=\$(cat /home/\$USER/.config/libreoffice/4/user/registrymodifications.xcu | grep 'PickList' | grep 'oor:name=\"0\"')
        if [[ \$(echo \$fileUsed | grep \"file\") ]] # on vérifie si le grep retourne un champ vide
        then
            if [[ ! \$(echo \$fileUsed | grep \"\$fileName\") ]] # on évite le doublon en comparant avec l'entrée précédente
            then
############### Début d'isolation du fichier modifié ##############
                fileUsed=\$(echo \$fileUsed | sed -e \"s/.*file:\/\///\") # on élimine le début
                fileUsed=\$(echo \"\${fileUsed%%<*}\") # On supprime la fin
                reEncoding
############### Fin d'isolation du fichier modifié ################


                deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\")
                if [[ ! \$(echo \$deja | grep \"\$fileUsed\") ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
                then
                    fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
                    extension=\$(echo \$fileName | sed \"s/.*\.//\")


################### Début de définition des extensions ############
                    if [[ \"\$extension\" = \"odt\" ]] || [[ \"\$extension\" = \"ott\" ]] || [[ \"\$extension\" = \"fodt\" ]] || [[ \"\$extension\" = \"uot\" ]] || [[ \"\$extension\" = \"doc\" ]] || [[ \"\$extension\" = \"docx\" ]] || [[ \"\$extension\" = \"dot\" ]] || [[ \"\$extension\" = \"rtf\" ]]
                    then
                        iconUsed=\"libreoffice-writer\"
                        applicationUsed=\"libreoffice --writer %U\"
                    elif [[ \"\$extension\" = \"odf\" ]] || [[ \"\$extension\" = \"mml\" ]]
                    then
                        iconUsed=\"libreoffice-math\"
                        applicationUsed=\"libreoffice --math %U\"
                    elif [[ \"\$extension\" = \"odp\" ]] || [[ \"\$extension\" = \"otp\" ]] || [[ \"\$extension\" = \"fodp\" ]] || [[ \"\$extension\" = \"uop\" ]] || [[ \"\$extension\" = \"ppt\" ]] || [[ \"\$extension\" = \"pptx\" ]] || [[ \"\$extension\" = \"ppsx\" ]] || [[ \"\$extension\" = \"potm\" ]] || [[ \"\$extension\" = \"pps\" ]] || [[ \"\$extension\" = \"pot\" ]]
                    then
                        iconUsed=\"libreoffice-impress\"
                        applicationUsed=\"libreoffice --impress %U\"
                    elif [[ \"\$extension\" = \"odg\" ]] || [[ \"\$extension\" = \"otg\" ]] || [[ \"\$extension\" = \"fodg\" ]]
                    then
                        iconUsed=\"libreoffice-draw\"
                        applicationUsed=\"libreoffice --draw %U\"
                    elif [[ \"\$extension\" = \"ods\" ]] || [[ \"\$extension\" = \"ots\" ]] || [[ \"\$extension\" = \"fods\" ]] || [[ \"\$extension\" = \"uos\" ]] || [[ \"\$extension\" = \"xlsx\" ]] || [[ \"\$extension\" = \"xls\" ]] || [[ \"\$extension\" = \"xlt\" ]] || [[ \"\$extension\" = \"csv\" ]]
                    then
                        iconUsed=\"libreoffice-calc\"
                        applicationUsed=\"libreoffice --calc %U\"
                    fi
################### Fin de définition des extensions ##############
                    moveList
                    createOne
                fi
            fi
        fi
        changed=1
    }
###################################################################
# Fin de la fonction de traitement de l'historique de libreoffice #
###################################################################


###############################################################
# Début de la fonction de traitement de l'historique de blender
###############################################################
    function recentlyBlender
    {
        fileUsed=\$(head -1 /home/\$USER/.config/blender/2.74/config/recent-files.txt)
        if [[ \$(echo \$fileUsed | grep \"/\") ]] # on vérifie si le grep retourne un champ vide
        then
            if [[ ! \$(echo \$fileUsed | grep \"\$fileName\") ]]
            then
                deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\")
                if [[ ! \$(echo \$deja | grep \"\$fileUsed\") ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
                then
                    fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
                    iconUsed=\"blender\"
                    applicationUsed=\"blender %f\"
                    moveList
                    createOne
                fi
            fi
        fi
        changed=1
    }
###############################################################
# Fin de la fonction de traitement de l'historique de blender #
###############################################################


#################################################################
# Début de la fonction de traitement de l'historique de darktable
#################################################################
    function recentlyDarktable
    {
####### Début de récupération de la date de modification ########
        toGrep=\$(date --date=\"1970-01-01 \$dateDarktable sec GMT\" \"+%Y:%m:%d %H:%M:%S\")
        toGrep=\"\${toGrep:0:18}\"
####### Fin de récupération de la date de modification ##########


####### Début de la récupération des données à traiter ##########
        fileUsed=\$(cat -v /home/\$USER/.config/darktable/library.db | grep \"\$toGrep\" | sed -e \"s/\^@//g\")
####### Fin de la récupération des données à traiter ############


        if [[ \$fileUsed ]] # on vérifie si le grep retourne un champ vide
        then


########### Début d'extraction du chemin du fichier ouvert ######
            fileUsed=\$(echo \$fileUsed | sed -e \"s/\$toGrep/§/\")
            position=\`expr index \"\$fileUsed\" §\`
            fileUsed=\${fileUsed:(\$position+1)} # on élimine le début
            fileUsed=\$(echo \$fileUsed | sed -e \"s/:/§/\")
            fileUsed=\$(echo \"\${fileUsed%%§*}\") # On supprime la fin
            lastFolder=\$(echo \$fileUsed | sed \"s/.*\///\")
            lastFolder=\${lastFolder:0:3} # on elimine la fin
            fileUsed=\$(echo \"\${fileUsed%/*}\")
            fileUsed=\$(find \"\$fileUsed\" -maxdepth 1 -name \$lastFolder*)
########### Fin d'extraction du chemin du fichier ouvert ########


            if [[ \$(echo \$fileUsed | grep \" \/\") ]] # Si il existe plusieurs dossiers ayant les mêmes 3 premières lettres
            then
############### Début d'extraction du dossier parent ############
                fileUsed=\$(echo \$fileUsed | sed -e \"s/ \//§/\")
                fileUsed=\$(echo \"\${fileUsed%%§*}\") # On supprime la fin
                fileUsed2=\$(echo \"\${fileUsed%/*}\")
############### Fin d'extraction du dossier parent ##############
            else # sinon, il n'y a qu'un seul dossier avec le meme début de nom
                fileUsed=\$(find \"\$fileUsed\" -maxdepth 1 -name \"*.xmp\" -mmin -1)
                fileUsed=\$(echo \$fileUsed | sed -e \"s/ /%20/g\")
                fileUsed=\$(echo \$fileUsed | sed -e \"s/%20\// \//\")
                fileUsed2=\$(echo \$fileUsed)
            fi


            for fileUsed in \$fileUsed2 # Pour chaque éléments séparés par un espace
            do
############### Début de finalisation du traitement #############
                fileUsed=\$(echo \$fileUsed | sed -e \"s/§/ /g\")
                fileUsed=\$(echo \$fileUsed | sed -e \"s/.xmp//g\")
                reEncoding
############### Fin de finalisation du traitement ###############


                deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\")
                if [[ ! \$(echo \$deja | grep \"\$fileUsed\") ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
                then
################### Début de création du raccourci ##############
                    fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
                    iconUsed=\"darktable\"
                    applicationUsed=\"darktable %U\"
                    moveList
                    createOne
################### Fin de création du raccourci ################
                fi
            done
        fi
        changed=1
    }
#################################################################
# Fin de la fonction de traitement de l'historique de darktable #
#################################################################


#################################################################
# Début de la fonction de traitement de l'historique de audacious
#################################################################
    function recentlyAudacious
    {
####### Début de la récupération des données à traiter ##########
        fileUsed=\$(cat /home/\$USER/.config/audacious/playlists/1000.audpl | grep \"uri=\")
####### Fin de la récupération des données à traiter ############


        if [[ \$(echo \$fileUsed | grep \"/\") ]] # on vérifie si le grep retourne un champ vide
        then


########### Début d'extraction du chemin du fichier ouvert ######
            fileUsed=\$(echo \$fileUsed | sed \"s/ uri=file:\/\//§/\")
            fileUsed=\$(echo \"\${fileUsed%%§*}\") # On supprime la fin
            fileUsed=\$(echo \$fileUsed | sed \"s/uri=file:\/\///\")
########### Fin d'extraction du chemin du fichier ouvert ########
            reEncoding


            if [[ ! \$(echo \$fileUsed | grep \"\$fileName\") ]]
            then


                deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\")
                if [[ ! \$(echo \$deja | grep \"\$fileUsed\") ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
                then
################### Début de création du raccourci ##############
                    fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
                    iconUsed=\"audacious\"
                    applicationUsed=\"audacious %U\"
                    moveList
                    createOne
################### Fin de création du raccourci ################
                fi
            fi
        fi
        changed=1
    }
#################################################################
# Fin de la fonction de traitement de l'historique de audacious #
#################################################################


################################################################
# Début de la fonction de traitement de l'historique de audacity
################################################################
    function recentlyAudacity
    {
        if [[ \$(ps -e | grep audacity) ]]
        then
########### Début du la récupération du repère #################
            fileUsed=\$(tail -1 /home/\$USER/.audacity-data/audacity.cfg)
            toGrep=\$(echo \$fileUsed | sed -e \"s/.*=//\") # on supprime le début
            toGrep=\$(echo \$toGrep | sed -e \"s/\//\\\\\\\\\//g\")
########### Fin du la récupération du repère ###################


        else


############### Début d'extraction du chemin du fichier ouvert #
                fileUsed=\$(cat -v /home/\$USER/.audacity-data/audacity.cfg)
                fileUsed=\$(echo \$fileUsed | sed -e \"s/.*\$toGrep //\") # on élimine le début
                fileUsed2=\$(echo \$fileUsed | sed -e \"s/ /%20/g\")
                fileUsed2=\$(echo \$fileUsed2 | sed -e \"s/%20file/ file/g\")
############### Fin d'extraction du chemin du fichier ouvert ###


            for fileUsed in \$fileUsed2 # Pour chaque éléments séparés par un espace
            do
############### Début de finalisation du traitement #############
                fileUsed=\$(echo \$fileUsed | sed -e \"s/.*=//\")
                reEncoding
############### Fin de finalisation du traitement ###############


                deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\")
                if [[ ! \$(echo \$deja | grep \"\$fileUsed\") ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
                then
################### Début de création du raccourci ##############
                    fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
                    iconUsed=\"audacity\"
                    applicationUsed=\"audacity %F\"
                    moveList
                    createOne
################### Fin de création du raccourci ################
                fi
            done
        fi
        changed=1
    }
################################################################
# Fin de la fonction de traitement de l'historique de audacity #
################################################################


###########################################################
# Début de la fonction de traitement de l'historique de vlc
###########################################################
    function recentlyVlc
    {
####### Début de la récupération des données à traiter ####
        fileUsed=\$(cat -v /home/\$USER/.config/vlc/vlc-qt-interface.conf | grep \"list=file\")
####### Fin de la récupération des données à traiter ######


        if [[ \$(echo \$fileUsed | grep \"/\") ]] # on vérifie si le grep retourne un champ vide
        then


########### Début d'extraction du chemin du fichier ouvert
            fileUsed=\$(echo \$fileUsed | sed \"s/list=file:\/\///\")
            fileUsed=\$(echo \$fileUsed | sed \"s/,/§/\")
            fileUsed=\$(echo \"\${fileUsed%§*}\") # On supprime la fin
########### Fin d'extraction du chemin du fichier ouvert ##
            reEncoding
            
            if [[ ! \$(echo \$fileUsed | grep \"\$fileName\") ]]
            then
                deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\")
                if [[ ! \$(echo \$deja | grep \"\$fileUsed\") ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
                then


################### Début de création du raccourci ########
                    fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
                    iconUsed=\"vlc\"
                    applicationUsed=\"/usr/bin/vlc --started-from-file %U\"
                    moveList
                    createOne
################### Fin de création du raccourci ##########
                fi
            fi
        fi
        changed=1
    }
###########################################################
# Fin de la fonction de traitement de l'historique de vlc #
###########################################################


############################################################
# Début de la fonction de traitement de l'historique général
############################################################
    function recentlyUsedXbel
    {
####### Début d'extraction de la dernière entrée ###########
        dateGeneralHistory2=\$((\$dateGeneralHistory-20))


        for ((i=0; i<20; i++))
        do
            dateGeneralHistory2=\$((\$dateGeneralHistory2+1))
            toGrep=\$(date --date=\"1970-01-01 \$dateGeneralHistory2 sec\" +%Y-%m-%dT%H:%M:%S)
            if [[ \$(cat /home/\$USER/.local/share/recently-used.xbel | grep \$toGrep) ]]
            then
                toTreat=\$(cat /home/\$USER/.local/share/recently-used.xbel | grep \$toGrep)
            fi
        done
####### Fin d'extraction de la dernière entrée #############


        if [[ \"\$toTreat\" = *\"bookmark\"* ]]
        then
            if [[ ! \$(echo \$toTreat | grep \"\$fileUsed\") ]] && [[ ! \$(echo \$toTreat | grep \"soffice\") ]] && [[ ! \$(echo \$toTreat | grep \"audacity\") ]]  && [[ ! \$(echo \$toTreat | grep \"darktable\") ]] # Si on retrouve le contenu de fileUsed dans toTreat, cela signifie que l'entrée précédente est la meme. on évite le doublon && si fileUsed contient soffice, ne pas s'executer && si fileUsed contient audacity, ne pas s'executer && si fileUsed contient darktable, ne pas s'executer
            then
############### Début d'isolation du fichier modifié #######
                fileUsed=\$(echo \$toTreat | sed -e \"s/.*file:\/\///\") # on supprime le début
                fileUsed=\$(echo \"\${fileUsed%%\\\"*}\") # On supprime la fin
                reEncoding # remplacement des codes caractères spéciaux du chemin vers le fichier
                if [ ! -f \"\$fileUsed\" ]
                then
                    fileUsed=\$(ls \$fileUsed.*)
                fi
############### Fin d'isolation du fichier modifié #########


                deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\")
                if [[ ! \$(echo \$deja | grep \"\$fileUsed\") ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
                then


################### Début d'extraction de la date modified #
                    toTreat=\$(echo \$toTreat | sed -e \"s/.*modified=\\\"//\") # on supprime le début
                    toTreat=\$(echo \"\${toTreat%%Z*}\") # On supprime la fin
                    toTreat=\$(cat /home/\$USER/.local/share/recently-used.xbel | grep \$toTreat)
################### Fin d'extraction de la date modified ###


################### Début d'isolation de l'application utilisé
                    applicationUsed=\$(echo \$toTreat | sed -e \"s/.*exec=\\\"&apos;//\") # on supprime le début
                    applicationUsed=\$(echo \"\${applicationUsed%%&*}\") # On supprime la fin
################### Fin d'isolation de l'application utilisé


                    if [[ \"\$applicationUsed\" = *\"gedit\"* ]]
                    then
                        iconUsed=\"accessories-text-editor\"
                    else
                        iconUsed=\$(echo \$applicationUsed | sed -e \"s/ %u//\")
                    fi


                    fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
                    moveList
                    createOne
                fi
            fi
        fi
        changed=1
    }
############################################################
# Fin de la fonction de traitement de l'historique général #
############################################################


#########################
# Début du script général
#########################
    while true
    do
        changed=0
        dateGeneralHistory=\$(stat -c %Y /home/\$USER/.local/share/recently-used.xbel)
        dateGeany=\$(stat -c %Y /home/\$USER/.config/geany/geany.conf)
        dateAbiword=\$(stat -c %Y /home/\$USER/.config/abiword/profile)
        dateAcrobat=\$(stat -c %Y /home/\$USER/.adobe/Acrobat/9.0/Preferences/reader_prefs)
        dateLibreoffice=\$(stat -c %Y /home/\$USER/.config/libreoffice/4/user/registrymodifications.xcu)
        if [[ -f /home/\$USER/.config/blender/2.74/config/recent-files.txt ]]
        then
            dateBlender=\$(stat -c %Y /home/\$USER/.config/blender/2.74/config/recent-files.txt)
        fi
        dateDarktable=\$(stat -c %Y /home/\$USER/.config/darktable/library.db)
        dateAudacious=\$(stat -c %Y /home/\$USER/.config/audacious/playlists/1000.audpl)
        dateAudacity=\$(stat -c %Y /home/\$USER/.audacity-data/audacity.cfg)
        dateVlc=\$(stat -c %Y /home/\$USER/.config/vlc/vlc-qt-interface.conf)


        if [[ \"\$dateGeany\" > \"\$dateReference\" ]]
        then
            recentlyGeany
        fi


        if [[ \"\$dateAbiword\" > \"\$dateReference\" ]]
        then
            recentlyAbiword
        fi


        if [[ \"\$dateAcrobat\" > \"\$dateReference\" ]]
        then
            recentlyAcrobat
        fi


        if [[ \"\$dateLibreoffice\" > \"\$dateReference\" ]]
        then
            recentlyLibreoffice
        fi


        if [[ \"\$dateBlender\" > \"\$dateReference\" ]]
        then
            recentlyBlender
        fi


        if [[ \"\$dateDarktable\" > \"\$dateReference\" ]]
        then
            recentlyDarktable
        fi


        if [[ \"\$dateAudacious\" > \"\$dateReference\" ]]
        then
            recentlyAudacious
        fi


        if [[ \"\$dateAudacity\" > \"\$dateReference\" ]]
        then
            recentlyAudacity
        fi


        if [[ \"\$dateVlc\" > \"\$dateReference\" ]]
        then
            recentlyVlc
        fi


        if [[ \"\$dateGeneralHistory\" > \"\$dateReference\" ]]
        then
            recentlyUsedXbel
        fi


        if [[ \$changed == 1 ]]
        then
            dateReference=\$(date +%s)
        fi
        sleep 0.5
    done
#########################
# Fin du script général #
#########################" > /opt/Recents/historique.sh


        echo "[Desktop Entry]
Name=Script historique
Comment=Script historique
Exec=bash /opt/Recents/historique.sh" > /etc/xdg/autostart/historique.desktop
    }
#####################################################
# Fin de la fonction crée le script de l'historique #
#####################################################


###################################
# Début d'execution du code général
###################################
    temp=$(whoami)
    if [[ "$temp" != "root" ]]
    then
        whiptail --title "sudoer" --msgbox "Le programme doit être exécuté avec les droits super-administrateur sudo" 8 78
    else
        if [ -f /usr/share/desktop-directories/historique.directory ]
        then
            whiptail --title "Supprimer?" --yesno "Voulez-vous supprimer l'historique du menu?" --yes-button "Oui" --no-button "Non" 8 78 3>&1 1>&2 2>&3
            if [[ "$?" == "0" ]]
            then
                cp /etc/xdg/lubuntu/menus/lxde-applications.menu.old /etc/xdg/lubuntu/menus/lxde-applications.menu
                rm /usr/share/desktop-directories/historique.directory
                rm /usr/share/desktop-directories/preferences-historique.directory
                rm -rf /opt/Recents/
                rm /usr/share/applications/nombre-elements.desktop
                rm /usr/share/applications/clear-history.desktop
                rm /etc/xdg/autostart/historique.desktop
            fi
        else
            creer_menu
            creer_conf
            creer_clear
            creer_historique
        fi
    fi
#################################
# Fin d'execution du code général
#################################



```

---

### Post by haitem-belgacem on 2016-02-26
bug fix vlc recent files and optimization

```
#!/bin/bash

#################################################################################
# Début de la fonction qui modifie le menu LXDE pour ajouter la partie Historique
#################################################################################
	function creer_menu
	{
####### Début de la sauvegarde ##################################################
		if [ ! -f /etc/xdg/lubuntu/menus/lxde-applications.menu.old ]
		then
			cp /etc/xdg/lubuntu/menus/lxde-applications.menu /etc/xdg/lubuntu/menus/lxde-applications.menu.old
		fi
####### Fin de la sauvegarde ####################################################


####### Début de l'ajout du menu Historique et des préférences ##################
		awk '/-- Applications Menu --/ { print; print "	<Menu>\n\
		<Name>Historique</Name>\n\
		<Directory>historique.directory</Directory>\n\
		<Include>\n\
			<And>\n\
				<Category>Historique</Category>\n\
			</And>\n\
		</Include>\n\
	</Menu>\n\
	<Menu>\n\
		<Name>PreferencesHistorique</Name>\n\
		<Directory>preferences-historique.directory</Directory>\n\
		<Include>\n\
			<And>\n\
				<Category>PreferencesHistorique</Category>\n\
			</And>\n\
		</Include>\n\
	</Menu>"; next }1' /etc/xdg/lubuntu/menus/lxde-applications.menu > /etc/xdg/lubuntu/menus/lxde-applications.menu2
		mv /etc/xdg/lubuntu/menus/lxde-applications.menu2 /etc/xdg/lubuntu/menus/lxde-applications.menu 
####### Fin de l'ajout du menu Historique et des préférences ####################


####### Début du placement des menus ############################################
		awk '/<Layout>/ { print; print "		<Menuname>Historique</Menuname>\n\
		<Menuname>PreferencesHistorique</Menuname>\n\
		<Separator/>"; next }1' /etc/xdg/lubuntu/menus/lxde-applications.menu > /etc/xdg/lubuntu/menus/lxde-applications.menu2
		mv /etc/xdg/lubuntu/menus/lxde-applications.menu2 /etc/xdg/lubuntu/menus/lxde-applications.menu
####### Fin du placement des menus ##############################################


####### Début de la création du sous-menu historique ############################
		echo "[Desktop Entry]
Name=Historique
Comment=Historique
Icon=document-open-recent
Type=Directory
X-Ubuntu-Gettext-Domain=gnome-menus-3.0" > /usr/share/desktop-directories/historique.directory
####### Fin de la création du sous-menu historique ##############################


####### Début de la création du sous-menu préférences de l'historique ###########
		echo "[Desktop Entry]
Name=Préférences historique
Comment=Préférences de l'historique
Icon=gnome-system
Type=Directory
X-Ubuntu-Gettext-Domain=gnome-menus-3.0" > /usr/share/desktop-directories/preferences-historique.directory
####### Fin de la création du sous-menu préférences de l'historique #############
	}
#################################################################################
# Fin de la fonction qui modifie le menu LXDE pour ajouter la partie Récents ####
#################################################################################


#############################################################################################
# Début de la fonction crée le script de configuration du nombre d'éléments dans l'historique
#############################################################################################
	function creer_conf
	{
####### Début de la création du script nombre d'éléments ####################################
		mkdir /opt/Recents
		echo "#!/bin/bash
if [ -f /home/\$USER/.nombre-elements.txt ]
then
	maxHistory=\$(tail /home/\$USER/.nombre-elements.txt)
else
	maxHistory=10
fi
nombre=\$(whiptail --title \"Nombre d'éléments dans l'historique\" --inputbox \"Combien d'éléments voulez-vous dans l'historique?\" 8 78 \$maxHistory 3>&1 1>&2 2>&3)


if [[ \$nombre < \$maxHistory ]]
then
	for ((i=\$maxHistory; i>\$nombre; i--))
		do
			rm /home/\$USER/.local/share/applications/\$i-history.desktop
		done
fi
echo \$nombre > /home/\$USER/.nombre-elements.txt" > /opt/Recents/nombre-elements.sh


####### Fin de la création du script nombre d'éléments ######################################


####### Début de la création du raccourci nombre d'éléments #################################
		echo "[Desktop Entry]
Encoding=UTF-8
Name=Nombre d'éléments
Comment=Indiquer le nombre d'éléments à afficher dans l'historique
Exec=lxterminal --command=\"bash /opt/Recents/nombre-elements.sh\"
Icon=gnome-system
Type=Application
Categories=PreferencesHistorique;" > /usr/share/applications/nombre-elements.desktop
####### Fin de la création du raccourci nombre d'éléments ###################################
	}
#############################################################################################
# Fin de la fonction crée le script de configuration du nombre d'éléments dans l'historique #
#############################################################################################


#####################################################################################
# Début de la fonction crée le script de purge du nombre d'éléments dans l'historique
#####################################################################################
	function creer_clear
	{
####### Début de la création du script clear ########################################
		echo "#!/bin/bash
rm /home/\$USER/.local/share/applications/*-history.desktop" > /opt/Recents/clear-history.sh
####### Fin de la création du script clear ##########################################


####### Début de la création du raccourci clear #####################################
		echo "[Desktop Entry]
Encoding=UTF-8
Name=Vider l'historique
Comment=Vide la liste des fichiers récents
Exec=lxterminal --command=\"bash /opt/Recents/clear-history.sh\"
Icon=edit-delete
Type=Application
Categories=PreferencesHistorique;" > /usr/share/applications/clear-history.desktop
####### Fin de la création du raccourci clear #######################################
	}
#####################################################################################
# Fin de la fonction crée le script de purge du nombre d'éléments dans l'historique #
#####################################################################################


#####################################################
# Début de la fonction crée le script de l'historique
#####################################################
	function creer_historique
	{
		echo "#!/bin/bash


#################################################
# Début de déclaration des variables essentielles
#################################################
	dateReference=\$(date +%s)
	maxHistory=\"10\"
	
	if [ ! -d /home/\$USER/.local/share/applications ]
	then
		mkdir /home/\$USER/.local/share/applications
	fi


	if [ ! -f /home/\$USER/.log/historique.log ]
	then
		touch /home/\$USER/.log/historique.log
	else
		rm /home/\$USER/.log/historique.log
		touch /home/\$USER/.log/historique.log
	fi


	fileUsed=\"§\"
	fileName=\"§\"
#################################################
# Fin de déclaration des variables essentielles #
#################################################


#####################################################
# Début de la fonction de ré-encondage des caractères
#####################################################
	function reEncoding
	{
		fileUsed=\$(echo \$fileUsed | sed \"s/%20/ /g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%80/À/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%82/Â/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%84/Ä/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%88/È/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%89/É/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%8A/Ê/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%8B/Ë/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%8E/Î/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%8F/Ï/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%94/Ô/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%96/Ö/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%9B/Û/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%9C/Ü/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%A0/à/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%A2/â/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%A4/ä/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%A7/ç/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%A8/è/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%A9/é/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%AA/ê/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%AB/ë/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%AE/î/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%AF/ï/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%B4/ô/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%B6/ö/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%B9/ù/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%BB/û/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%BC/ü/g\")
	}
#####################################################
# Fin de la fonction de ré-encondage des caractères #
#####################################################


################################################
# Début de la fonction décalement des raccourcis
################################################
	function moveList
	{
		if [ -f /home/\$USER/.nombre-elements.txt ]
		then
			maxHistory=\$(tail /home/\$USER/.nombre-elements.txt)
		fi
		
		for ((i=\$maxHistory; i>1; i--))
		do
			j=\$((i-1))
			move=\$(mv /home/\$USER/.local/share/applications/\$j-history.desktop /home/\$USER/.local/share/applications/\$i-history.desktop)
		done
	}
################################################
# Fin de la fonction décalement des raccourcis #
################################################


#######################################################
# Début de la fonction d'écriture du raccourci numéro 1
#######################################################
	function createOne
	{
		if [ ! -f /home/\$USER/.local/share/applications/1-history.desktop ]
		then
			touch /home/\$USER/.local/share/applications/1-history.desktop
		fi
		
		echo \"[Desktop Entry]
Name=\$fileName
Comment=\$fileUsed
Exec=\$applicationUsed \\\"\$fileUsed\\\"
Icon=\$iconUsed
Type=Application
Categories=Historique;\" > /home/\$USER/.local/share/applications/1-history.desktop
	}
#######################################################
# Fin de la fonction d'écriture du raccourci numéro 1 #
#######################################################


#############################################################
# Début de la fonction de traitement de l'historique de geany
#############################################################
	function recentlyGeany
	{
		fileUsed=\$(tail /home/\$USER/.config/geany/geany.conf | grep \"recent_files=\")


########### Début d'isolation du fichier modifié ############
		fileUsed=\$(echo \"\${fileUsed%%;*}\") # On supprime la fin
		fileUsed=\$(echo \$fileUsed | sed -e \"s/recent_files=//\")
		echo \"\$(date) -> recentlyGeany -> fileUsed -> \$fileUsed\" >> /home/\$USER/.log/historique.log
########### Fin d'isolation du fichier modifié ##############


		deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\" | grep geany)
		echo \"\$(date) -> recentlyGeany -> deja -> \$deja\" >> /home/\$USER/.log/historique.log
		if [[ ! \$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\" | grep geany) ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
		then
			echo \"\$(date) -> recentlyGeany -> PAS DE DOUBLON\" >> /home/\$USER/.log/historique.log
			fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
			iconUsed=\"geany\"
			applicationUsed=\"geany %u\"
			moveList
			createOne
		else
			echo \"\$(date) -> recentlyGeany -> UN DOUBLON\" >> /home/\$USER/.log/historique.log
		fi
		changed=1
	}
#############################################################
# Fin de la fonction de traitement de l'historique de geany #
#############################################################


###############################################################
# Début de la fonction de traitement de l'historique de abiword
###############################################################
	function recentlyAbiword
	{
		fileUsed=\$(cat /home/\$USER/.config/abiword/profile | grep \"name1=\")
		if [[ ! \$(echo \$fileUsed | grep \"\$fileName\") ]]
		then
########### Début d'isolation du fichier modifié ##############
			fileUsed=\$(echo \$fileUsed | sed -e \"s/\\\"//g\")
			fileUsed=\$(echo \$fileUsed | sed -e \"s/name1=file:\/\///\")
			echo \"\$(date) -> recentlyAbiword -> fileUsed -> \$fileUsed\" >> /home/\$USER/.log/historique.log
########### Fin d'isolation du fichier modifié ################


			deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\" | grep abiword)
			echo \"\$(date) -> recentlyAbiword -> deja -> \$deja\" >> /home/\$USER/.log/historique.log
			if [[ ! \$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\" | grep abiword) ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
			then
				echo \"\$(date) -> recentlyAbiword -> PAS DE DOUBLON\" >> /home/\$USER/.log/historique.log
				fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
				iconUsed=\"abiword\"
				applicationUsed=\"abiword %u\"
				moveList
				createOne
			else
				echo \"\$(date) -> recentlyAbiword -> UN DOUBLON\" >> /home/\$USER/.log/historique.log
			fi
		fi
		changed=1
	}
###############################################################
# Fin de la fonction de traitement de l'historique de abiword #
###############################################################


###############################################################
# Début de la fonction de traitement de l'historique de acrobat
###############################################################
	function recentlyAcrobat
	{
		fileUsed=\$(cat -v /home/\$USER/.adobe/Acrobat/9.0/Preferences/reader_prefs | grep \"/RecentFiles\")
		if [[ ! \$(echo \$fileUsed | grep \"\$fileName\") ]]
		then
########### Début d'isolation du fichier modifié ##############
			fileUsed=\$(echo \$fileUsed | sed -e \"s/.*[(]//\") # on élimine le début
			fileUsed=\$(echo \$fileUsed | sed -e \"s/[)]\]//\") # on élimine la fin
			echo \"\$(date) -> recentlyAcrobat -> fileUsed -> \$fileUsed\" >> /home/\$USER/.log/historique.log
########### Fin d'isolation du fichier modifié ################


			deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\" | grep acroread)
			echo \"\$(date) -> recentlyAcrobat -> deja -> \$deja\" >> /home/\$USER/.log/historique.log
			if [[ ! \$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\" | grep acroread) ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
			then
				echo \"\$(date) -> recentlyAcrobat -> PAS DE DOUBLON\" >> /home/\$USER/.log/historique.log
				fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
				iconUsed=\"AdobeReader9\"
				applicationUsed=\"acroread\"
				moveList
				createOne
			else
				echo \"\$(date) -> recentlyAcrobat -> UN DOUBLON\" >> /home/\$USER/.log/historique.log
			fi
		fi
		changed=1
	}
###############################################################
# Fin de la fonction de traitement de l'historique de acrobat #
###############################################################


###################################################################
# Début de la fonction de traitement de l'historique de libreoffice
###################################################################
	function recentlyLibreoffice
	{
		fileUsed=\$(cat /home/\$USER/.config/libreoffice/4/user/registrymodifications.xcu | grep 'PickList' | grep 'oor:name=\"0\"')
		if [[ \$(echo \$fileUsed | grep \"file\") ]] # on vérifie si le grep retourne un champ vide
		then
			if [[ ! \$(echo \$fileUsed | grep \"\$fileName\") ]] # on évite le doublon en comparant avec l'entrée précédente
			then
############### Début d'isolation du fichier modifié ##############
				fileUsed=\$(echo \$fileUsed | sed -e \"s/.*file:\/\///\") # on élimine le début
				fileUsed=\$(echo \"\${fileUsed%%<*}\") # On supprime la fin
				reEncoding
				echo \"\$(date) -> recentlyLibreoffice -> fileUsed -> \$fileUsed\" >> /home/\$USER/.log/historique.log
############### Fin d'isolation du fichier modifié ################


				deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\" | grep libreoffice)
				echo \"\$(date) -> recentlyLibreoffice -> deja -> \$deja\" >> /home/\$USER/.log/historique.log
				if [[ ! \$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\" | grep libreoffice) ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
				then
					echo \"\$(date) -> recentlyLibreoffice -> PAS DE DOUBLON\" >> /home/\$USER/.log/historique.log
					fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
					extension=\$(echo \$fileName | sed \"s/.*\.//\")


################### Début de définition des extensions ############
					if [[ \"\$extension\" = \"odt\" ]] || [[ \"\$extension\" = \"ott\" ]] || [[ \"\$extension\" = \"fodt\" ]] || [[ \"\$extension\" = \"uot\" ]] || [[ \"\$extension\" = \"doc\" ]] || [[ \"\$extension\" = \"docx\" ]] || [[ \"\$extension\" = \"dot\" ]] || [[ \"\$extension\" = \"rtf\" ]]
					then
						iconUsed=\"libreoffice-writer\"
						applicationUsed=\"libreoffice --writer %U\"
					elif [[ \"\$extension\" = \"odf\" ]] || [[ \"\$extension\" = \"mml\" ]]
					then
						iconUsed=\"libreoffice-math\"
						applicationUsed=\"libreoffice --math %U\"
					elif [[ \"\$extension\" = \"odp\" ]] || [[ \"\$extension\" = \"otp\" ]] || [[ \"\$extension\" = \"fodp\" ]] || [[ \"\$extension\" = \"uop\" ]] || [[ \"\$extension\" = \"ppt\" ]] || [[ \"\$extension\" = \"pptx\" ]] || [[ \"\$extension\" = \"ppsx\" ]] || [[ \"\$extension\" = \"potm\" ]] || [[ \"\$extension\" = \"pps\" ]] || [[ \"\$extension\" = \"pot\" ]]
					then
						iconUsed=\"libreoffice-impress\"
						applicationUsed=\"libreoffice --impress %U\"
					elif [[ \"\$extension\" = \"odg\" ]] || [[ \"\$extension\" = \"otg\" ]] || [[ \"\$extension\" = \"fodg\" ]]
					then
						iconUsed=\"libreoffice-draw\"
						applicationUsed=\"libreoffice --draw %U\"
					elif [[ \"\$extension\" = \"ods\" ]] || [[ \"\$extension\" = \"ots\" ]] || [[ \"\$extension\" = \"fods\" ]] || [[ \"\$extension\" = \"uos\" ]] || [[ \"\$extension\" = \"xlsx\" ]] || [[ \"\$extension\" = \"xls\" ]] || [[ \"\$extension\" = \"xlt\" ]] || [[ \"\$extension\" = \"csv\" ]]
					then
						iconUsed=\"libreoffice-calc\"
						applicationUsed=\"libreoffice --calc %U\"
					fi
################### Fin de définition des extensions ##############
					moveList
					createOne
				else
					echo \"\$(date) -> recentlyLibreoffice -> UN DOUBLON\" >> /home/\$USER/.log/historique.log
				fi
			fi
		fi
		changed=1
	}
###################################################################
# Fin de la fonction de traitement de l'historique de libreoffice #
###################################################################


###############################################################
# Début de la fonction de traitement de l'historique de blender
###############################################################
	function recentlyBlender
	{
		fileUsed=\$(head -1 /home/\$USER/.config/blender/2.74/config/recent-files.txt)
		echo \"\$(date) -> recentlyBlender -> fileUsed -> \$fileUsed\" >> /home/\$USER/.log/historique.log
		if [[ \$(echo \$fileUsed | grep \"/\") ]] # on vérifie si le grep retourne un champ vide
		then
			if [[ ! \$(echo \$fileUsed | grep \"\$fileName\") ]]
			then
				deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\" | grep blender)
				echo \"\$(date) -> recentlyBlender -> deja -> \$deja\" >> /home/\$USER/.log/historique.log
				if [[ ! \$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\" | grep blender) ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
				then
					echo \"\$(date) -> recentlyBlender -> PAS DE DOUBLON\" >> /home/\$USER/.log/historique.log
					fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
					iconUsed=\"blender\"
					applicationUsed=\"blender %f\"
					moveList
					createOne
				else
					echo \"\$(date) -> recentlyBlender -> UN DOUBLON\" >> /home/\$USER/.log/historique.log
				fi
			fi
		fi
		changed=1
	}
###############################################################
# Fin de la fonction de traitement de l'historique de blender #
###############################################################


#################################################################
# Début de la fonction de traitement de l'historique de darktable
#################################################################
	function recentlyDarktable
	{
####### Début de récupération de la date de modification ########
		toGrep=\$(date --date=\"1970-01-01 \$dateDarktable sec GMT\" \"+%Y:%m:%d %H:%M:%S\")
		toGrep=\"\${toGrep:0:18}\"
		echo \"\$(date) -> recentlyDarktable -> toGrep -> \$toGrep\" >> /home/\$USER/.log/historique.log
####### Fin de récupération de la date de modification ##########


####### Début de la récupération des données à traiter ##########
		fileUsed=\$(cat -v /home/\$USER/.config/darktable/library.db | grep \"\$toGrep\" | sed -e \"s/\^@//g\")
####### Fin de la récupération des données à traiter ############


		if [[ \$fileUsed ]] # on vérifie si le grep retourne un champ vide
		then


########### Début d'extraction du chemin du fichier ouvert ######
			fileUsed=\$(echo \$fileUsed | sed -e \"s/\$toGrep/§/\")
			position=\`expr index \"\$fileUsed\" §\`
			fileUsed=\${fileUsed:(\$position+1)} # on élimine le début
			fileUsed=\$(echo \$fileUsed | sed -e \"s/:/§/\")
			fileUsed=\$(echo \"\${fileUsed%%§*}\") # On supprime la fin
			lastFolder=\$(echo \$fileUsed | sed \"s/.*\///\")
			lastFolder=\${lastFolder:0:3} # on elimine la fin
			fileUsed=\$(echo \"\${fileUsed%/*}\")
			fileUsed=\$(find \"\$fileUsed\" -maxdepth 1 -name \$lastFolder*)
			echo \"\$(date) -> recentlyDarktable -> fileUsed -> \$fileUsed\" >> /home/\$USER/.log/historique.log
########### Fin d'extraction du chemin du fichier ouvert ########


			if [[ \$(echo \$fileUsed | grep \" \/\") ]] # Si il existe plusieurs dossiers ayant les mêmes 3 premières lettres
			then
############### Début d'extraction du dossier parent ############
				fileUsed=\$(echo \$fileUsed | sed -e \"s/ \//§/\")
				fileUsed=\$(echo \"\${fileUsed%%§*}\") # On supprime la fin
				echo \"\$(date) -> recentlyDarktable -> fileUsed -> \$fileUsed\" >> /home/\$USER/.log/historique.log
				fileUsed2=\$(echo \"\${fileUsed%/*}\")
				echo \"\$(date) -> recentlyDarktable -> fileUsed2 -> \$fileUsed2\" >> /home/\$USER/.log/historique.log
############### Fin d'extraction du dossier parent ##############
			else # sinon, il n'y a qu'un seul dossier avec le meme début de nom
				fileUsed=\$(find \"\$fileUsed\" -maxdepth 1 -name \"*.xmp\" -mmin -1)
				fileUsed=\$(echo \$fileUsed | sed -e \"s/ /%20/g\")
				fileUsed=\$(echo \$fileUsed | sed -e \"s/%20\// \//\")
				echo \"\$(date) -> recentlyDarktable -> fileUsed -> \$fileUsed\" >> /home/\$USER/.log/historique.log
				fileUsed2=\$(echo \$fileUsed)
				echo \"\$(date) -> recentlyDarktable -> fileUsed2 -> \$fileUsed2\" >> /home/\$USER/.log/historique.log
			fi


			for fileUsed in \$fileUsed2 # Pour chaque éléments séparés par un espace
			do
############### Début de finalisation du traitement #############
				fileUsed=\$(echo \$fileUsed | sed -e \"s/§/ /g\")
				fileUsed=\$(echo \$fileUsed | sed -e \"s/.xmp//g\")
				reEncoding
				echo \"\$(date) -> recentlyDarktable -> fileUsed -> \$fileUsed\" >> /home/\$USER/.log/historique.log
############### Fin de finalisation du traitement ###############


				deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\" | grep darktable)
				echo \"\$(date) -> recentlyDarktable -> deja -> \$deja\" >> /home/\$USER/.log/historique.log
				if [[ ! \$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\" | grep darktable) ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
				then
################### Début de création du raccourci ##############
					echo \"\$(date) -> recentlyDarktable -> PAS DE DOUBLON\" >> /home/\$USER/.log/historique.log
					fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
					iconUsed=\"darktable\"
					applicationUsed=\"darktable %U\"
					moveList
					createOne
################### Fin de création du raccourci ################
				else
					echo \"\$(date) -> recentlyDarktable -> UN DOUBLON\" >> /home/\$USER/.log/historique.log
				fi
			done
		fi
		changed=1
	}
#################################################################
# Fin de la fonction de traitement de l'historique de darktable #
#################################################################


#################################################################
# Début de la fonction de traitement de l'historique de audacious
#################################################################
	function recentlyAudacious
	{
####### Début de la récupération des données à traiter ##########
		fileUsed=\$(cat /home/\$USER/.config/audacious/playlists/1000.audpl | grep \"uri=\")
####### Fin de la récupération des données à traiter ############


		if [[ \$(echo \$fileUsed | grep \"/\") ]] # on vérifie si le grep retourne un champ vide
		then


########### Début d'extraction du chemin du fichier ouvert ######
			fileUsed=\$(echo \$fileUsed | sed \"s/ uri=file:\/\//§/\")
			fileUsed=\$(echo \"\${fileUsed%%§*}\") # On supprime la fin
			fileUsed=\$(echo \$fileUsed | sed \"s/uri=file:\/\///\")
			reEncoding
			echo \"\$(date) -> recentlyAudacious -> fileUsed -> \$fileUsed\" >> /home/\$USER/.log/historique.log
########### Fin d'extraction du chemin du fichier ouvert ########


			deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\" | grep audacious)
			echo \"\$(date) -> recentlyAudacious -> deja -> \$deja\" >> /home/\$USER/.log/historique.log
			if [[ ! \$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\" | grep audacious) ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
			then
################### Début de création du raccourci ##############
				echo \"\$(date) -> recentlyAudacious -> PAS DE DOUBLON\" >> /home/\$USER/.log/historique.log
				fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
				iconUsed=\"audacious\"
				applicationUsed=\"audacious %U\"
				moveList
				createOne
################### Fin de création du raccourci ################
			else
				echo \"\$(date) -> recentlyAudacious -> UN DOUBLON\" >> /home/\$USER/.log/historique.log
			fi
		fi
		changed=1
	}
#################################################################
# Fin de la fonction de traitement de l'historique de audacious #
#################################################################


################################################################
# Début de la fonction de traitement de l'historique de audacity
################################################################
	function recentlyAudacity
	{
		if [[ \$(ps -e | grep audacity) ]]
		then
########### Début du la récupération du repère #################
			fileUsed=\$(tail -1 /home/\$USER/.audacity-data/audacity.cfg)
			toGrep=\$(echo \$fileUsed | sed -e \"s/.*=//\") # on supprime le début
			toGrep=\$(echo \$toGrep | sed -e \"s/\//\\\\\\\\\//g\")
			echo \"\$(date) -> recentlyAudacity -> toGrep -> \$toGrep\" >> /home/\$USER/.log/historique.log
########### Fin du la récupération du repère ###################


		else


############### Début d'extraction du chemin du fichier ouvert #
				fileUsed=\$(cat -v /home/\$USER/.audacity-data/audacity.cfg)
				fileUsed=\$(echo \$fileUsed | sed -e \"s/.*\$toGrep //\") # on élimine le début
				echo \"\$(date) -> recentlyAudacity -> fileUsed -> \$fileUsed\" >> /home/\$USER/.log/historique.log
				fileUsed2=\$(echo \$fileUsed | sed -e \"s/ /%20/g\")
				fileUsed2=\$(echo \$fileUsed2 | sed -e \"s/%20file/ file/g\")
				echo \"\$(date) -> recentlyAudacity -> fileUsed2 -> \$fileUsed2\" >> /home/\$USER/.log/historique.log
############### Fin d'extraction du chemin du fichier ouvert ###


			for fileUsed in \$fileUsed2 # Pour chaque éléments séparés par un espace
			do
############### Début de finalisation du traitement #############
				fileUsed=\$(echo \$fileUsed | sed -e \"s/.*=//\")
				reEncoding
				echo \"\$(date) -> recentlyAudacity -> fileUsed -> \$fileUsed\" >> /home/\$USER/.log/historique.log
############### Fin de finalisation du traitement ###############


				deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\" | grep audacity)
				echo \"\$(date) -> recentlyAudacity -> deja -> \$deja\" >> /home/\$USER/.log/historique.log
				if [[ ! \$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\" | grep audacity) ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
				then
################### Début de création du raccourci ##############
					echo \"\$(date) -> recentlyAudacity -> PAS DE DOUBLON\" >> /home/\$USER/.log/historique.log
					fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
					iconUsed=\"audacity\"
					applicationUsed=\"audacity %F\"
					moveList
					createOne
################### Fin de création du raccourci ################
				else
					echo \"\$(date) -> recentlyAudacity -> UN DOUBLON\" >> /home/\$USER/.log/historique.log
				fi
			done
		fi
		changed=1
	}
################################################################
# Fin de la fonction de traitement de l'historique de audacity #
################################################################


###########################################################
# Début de la fonction de traitement de l'historique de vlc
###########################################################
	function recentlyVlc
	{
####### Début de la récupération des données à traiter ####
		fileUsed=\$(cat /home/\$USER/.config/vlc/vlc-qt-interface.conf | grep \"list=\\\"file\")
		fileUsed=\$(echo \$fileUsed | sed \"s/\\\"//g\")
####### Fin de la récupération des données à traiter ######


		if [[ \$(echo \$fileUsed | grep \"/\") ]] # on vérifie si le grep retourne un champ vide
		then


########### Début d'extraction du chemin du fichier ouvert
			fileUsed=\$(echo \$fileUsed | sed \"s/list=file:\/\///\")
			fileUsed=\$(echo \$fileUsed | sed \"s/, file/§/\")
			fileUsed=\$(echo \"\${fileUsed%§*}\") # On supprime la fin
			reEncoding
			echo \"\$(date) -> recentlyVlc -> fileUsed -> \$fileUsed\" >> /home/\$USER/.log/historique.log
########### Fin d'extraction du chemin du fichier ouvert ##


			deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\" | grep vlc)
			echo \"\$(date) -> recentlyVlc -> deja -> \$deja\" >> /home/\$USER/.log/historique.log
			if [[ ! \$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\" | grep vlc) ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
			then


################### Début de création du raccourci ########
				echo \"\$(date) -> recentlyVlc -> PAS DE DOUBLON\" >> /home/\$USER/.log/historique.log
				fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
				iconUsed=\"vlc\"
				applicationUsed=\"/usr/bin/vlc --started-from-file %U\"
				moveList
				createOne
################### Fin de création du raccourci ##########
			else
				echo \"\$(date) -> recentlyVlc -> UN DOUBLON\" >> /home/\$USER/.log/historique.log
			fi
		fi
		changed=1
	}
###########################################################
# Fin de la fonction de traitement de l'historique de vlc #
###########################################################


############################################################
# Début de la fonction de traitement de l'historique général
############################################################
	function recentlyUsedXbel
	{
####### Début d'extraction de la dernière entrée ###########
		dateGeneralHistory2=\$((\$dateGeneralHistory-20))


		for ((i=0; i<20; i++))
		do
			dateGeneralHistory2=\$((\$dateGeneralHistory2+1))
			toGrep=\$(date --date=\"1970-01-01 \$dateGeneralHistory2 sec\" +%Y-%m-%dT%H:%M:%S)
			if [[ \$(cat /home/\$USER/.local/share/recently-used.xbel | grep \$toGrep) ]]
			then
				toTreat=\$(cat /home/\$USER/.local/share/recently-used.xbel | grep \$toGrep)
				echo \"\$(date) -> recentlyUsedXbel -> toTreat -> \$toTreat\" >> /home/\$USER/.log/historique.log
			fi
		done
####### Fin d'extraction de la dernière entrée #############


		if [[ \"\$toTreat\" = *\"bookmark\"* ]]
		then
			if [[ ! \$(echo \$toTreat | grep \"soffice\") ]] && [[ ! \$(echo \$toTreat | grep \"audacity\") ]]  && [[ ! \$(echo \$toTreat | grep \"darktable\") ]] # Si on retrouve le contenu de fileUsed dans toTreat, cela signifie que l'entrée précédente est la meme. on évite le doublon && si fileUsed contient soffice, ne pas s'executer && si fileUsed contient audacity, ne pas s'executer && si fileUsed contient darktable, ne pas s'executer
			then
############### Début d'isolation du fichier modifié #######
				fileUsed=\$(echo \$toTreat | sed -e \"s/.*file:\/\///\") # on supprime le début
				fileUsed=\$(echo \"\${fileUsed%%\\\"*}\") # On supprime la fin
				reEncoding # remplacement des codes caractères spéciaux du chemin vers le fichier
				echo \"\$(date) -> recentlyUsedXbel -> fileUsed -> \$fileUsed\" >> /home/\$USER/.log/historique.log
				if [ ! -f \"\$fileUsed\" ]
				then
					fileUsed=\$(ls \$fileUsed.*)
					echo \"\$(date) -> recentlyUsedXbel -> fileUsed -> \$fileUsed\" >> /home/\$USER/.log/historique.log
				fi
############### Fin d'isolation du fichier modifié #########


				deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$fileUsed\")
				echo \"\$(date) -> recentlyUsedXbel -> deja -> \$deja\" >> /home/\$USER/.log/historique.log
				if [[ ! \$(echo \$deja | grep \"\$fileUsed\") ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
				then


################### Début d'extraction de la date modified #
					toTreat=\$(echo \$toTreat | sed -e \"s/.*modified=\\\"//\") # on supprime le début
					toTreat=\$(echo \"\${toTreat%%Z*}\") # On supprime la fin
					toTreat=\$(cat /home/\$USER/.local/share/recently-used.xbel | grep \$toTreat)
					echo \"\$(date) -> recentlyUsedXbel -> toTreat -> \$toTreat\" >> /home/\$USER/.log/historique.log
################### Fin d'extraction de la date modified ###


################### Début d'isolation de l'application utilisé
					applicationUsed=\$(echo \$toTreat | sed -e \"s/.*exec=\\\"&apos;//\") # on supprime le début
					applicationUsed=\$(echo \"\${applicationUsed%%&*}\") # On supprime la fin
					echo \"\$(date) -> recentlyUsedXbel -> applicationUsed -> \$applicationUsed\" >> /home/\$USER/.log/historique.log
################### Fin d'isolation de l'application utilisé


					if [[ \"\$applicationUsed\" = *\"gedit\"* ]]
					then
						iconUsed=\"accessories-text-editor\"
					else
						iconUsed=\$(echo \$applicationUsed | sed -e \"s/ %u//\")
					fi


					fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
					moveList
					createOne
					echo \"\$(date) -> recentlyUsedXbel -> CREATION LISTE GENERALE\" >> /home/\$USER/.log/historique.log
				fi
			fi
		fi
		changed=1
	}
############################################################
# Fin de la fonction de traitement de l'historique général #
############################################################


#########################
# Début du script général
#########################
	while true
	do
		changed=0
		dateGeneralHistory=\$(stat -c %Y /home/\$USER/.local/share/recently-used.xbel)
		dateGeany=\$(stat -c %Y /home/\$USER/.config/geany/geany.conf)
		dateAbiword=\$(stat -c %Y /home/\$USER/.config/abiword/profile)
		dateAcrobat=\$(stat -c %Y /home/\$USER/.adobe/Acrobat/9.0/Preferences/reader_prefs)
		dateLibreoffice=\$(stat -c %Y /home/\$USER/.config/libreoffice/4/user/registrymodifications.xcu)
		if [[ -f /home/\$USER/.config/blender/2.74/config/recent-files.txt ]]
		then
			dateBlender=\$(stat -c %Y /home/\$USER/.config/blender/2.74/config/recent-files.txt)
		fi
		dateDarktable=\$(stat -c %Y /home/\$USER/.config/darktable/library.db)
		dateAudacious=\$(stat -c %Y /home/\$USER/.config/audacious/playlists/1000.audpl)
		dateAudacity=\$(stat -c %Y /home/\$USER/.audacity-data/audacity.cfg)
		dateVlc=\$(stat -c %Y /home/\$USER/.config/vlc/vlc-qt-interface.conf)


		if [[ \"\$dateGeany\" > \"\$dateReference\" ]]
		then
			recentlyGeany
		fi


		if [[ \"\$dateAbiword\" > \"\$dateReference\" ]]
		then
			recentlyAbiword
		fi


		if [[ \"\$dateAcrobat\" > \"\$dateReference\" ]]
		then
			recentlyAcrobat
		fi


		if [[ \"\$dateLibreoffice\" > \"\$dateReference\" ]]
		then
			recentlyLibreoffice
		fi


		if [[ \"\$dateBlender\" > \"\$dateReference\" ]]
		then
			recentlyBlender
		fi


		if [[ \"\$dateDarktable\" > \"\$dateReference\" ]]
		then
			recentlyDarktable
		fi


		if [[ \"\$dateAudacious\" > \"\$dateReference\" ]]
		then
			recentlyAudacious
		fi


		if [[ \"\$dateAudacity\" > \"\$dateReference\" ]]
		then
			recentlyAudacity
		fi


		if [[ \"\$dateVlc\" > \"\$dateReference\" ]]
		then
			recentlyVlc
		fi


		if [[ \"\$dateGeneralHistory\" > \"\$dateReference\" ]]
		then
			recentlyUsedXbel
		fi


		if [[ \$changed == 1 ]]
		then
			dateReference=\$(date +%s)
		fi
		sleep 0.5
	done
#########################
# Fin du script général #
#########################" > /opt/Recents/historique.sh


		echo "[Desktop Entry]
Name=Script historique
Comment=Script historique
Exec=bash /opt/Recents/historique.sh" > /etc/xdg/autostart/historique.desktop
	}
#####################################################
# Fin de la fonction crée le script de l'historique #
#####################################################


###################################
# Début d'execution du code général
###################################
	temp=$(whoami)
	if [[ "$temp" != "root" ]]
	then
		whiptail --title "sudoer" --msgbox "Le programme doit être exécuté avec les droits super-administrateur sudo" 8 78
	else
		if [ -f /usr/share/desktop-directories/historique.directory ]
		then
			whiptail --title "Supprimer?" --yesno "Voulez-vous supprimer l'historique du menu?" --yes-button "Oui" --no-button "Non" 8 78 3>&1 1>&2 2>&3
			if [[ "$?" == "0" ]]
			then
				cp /etc/xdg/lubuntu/menus/lxde-applications.menu.old /etc/xdg/lubuntu/menus/lxde-applications.menu
				rm /usr/share/desktop-directories/historique.directory
				rm /usr/share/desktop-directories/preferences-historique.directory
				rm -rf /opt/Recents/
				rm /usr/share/applications/nombre-elements.desktop
				rm /usr/share/applications/clear-history.desktop
				rm /etc/xdg/autostart/historique.desktop
			fi
		else
			creer_menu
			creer_conf
			creer_clear
			creer_historique
		fi
	fi
#################################
# Fin d'execution du code général
#################################



```

---

### Post by haitem-belgacem on 2016-03-03
Correction : taking into account file names with brackets "[]"


```
#!/bin/bash


#################################################################################
# Début de la fonction qui modifie le menu LXDE pour ajouter la partie Historique
#################################################################################
	function creer_menu
	{
####### Début de la sauvegarde ##################################################
		if [ ! -f /etc/xdg/lubuntu/menus/lxde-applications.menu.old ]
		then
			cp /etc/xdg/lubuntu/menus/lxde-applications.menu /etc/xdg/lubuntu/menus/lxde-applications.menu.old
		fi
####### Fin de la sauvegarde ####################################################


####### Début de l'ajout du menu Historique et des préférences ##################
		awk '/-- Applications Menu --/ { print; print "	<Menu>\n\
		<Name>Historique</Name>\n\
		<Directory>historique.directory</Directory>\n\
		<Include>\n\
			<And>\n\
				<Category>Historique</Category>\n\
			</And>\n\
		</Include>\n\
	</Menu>\n\
	<Menu>\n\
		<Name>PreferencesHistorique</Name>\n\
		<Directory>preferences-historique.directory</Directory>\n\
		<Include>\n\
			<And>\n\
				<Category>PreferencesHistorique</Category>\n\
			</And>\n\
		</Include>\n\
	</Menu>"; next }1' /etc/xdg/lubuntu/menus/lxde-applications.menu > /etc/xdg/lubuntu/menus/lxde-applications.menu2
		mv /etc/xdg/lubuntu/menus/lxde-applications.menu2 /etc/xdg/lubuntu/menus/lxde-applications.menu 
####### Fin de l'ajout du menu Historique et des préférences ####################


####### Début du placement des menus ############################################
		awk '/<Layout>/ { print; print "		<Menuname>Historique</Menuname>\n\
		<Menuname>PreferencesHistorique</Menuname>\n\
		<Separator/>"; next }1' /etc/xdg/lubuntu/menus/lxde-applications.menu > /etc/xdg/lubuntu/menus/lxde-applications.menu2
		mv /etc/xdg/lubuntu/menus/lxde-applications.menu2 /etc/xdg/lubuntu/menus/lxde-applications.menu
####### Fin du placement des menus ##############################################


####### Début de la création du sous-menu historique ############################
		echo "[Desktop Entry]
Name=Historique
Comment=Historique
Icon=document-open-recent
Type=Directory
X-Ubuntu-Gettext-Domain=gnome-menus-3.0" > /usr/share/desktop-directories/historique.directory
####### Fin de la création du sous-menu historique ##############################


####### Début de la création du sous-menu préférences de l'historique ###########
		echo "[Desktop Entry]
Name=Préférences historique
Comment=Préférences de l'historique
Icon=gnome-system
Type=Directory
X-Ubuntu-Gettext-Domain=gnome-menus-3.0" > /usr/share/desktop-directories/preferences-historique.directory
####### Fin de la création du sous-menu préférences de l'historique #############
	}
#################################################################################
# Fin de la fonction qui modifie le menu LXDE pour ajouter la partie Récents ####
#################################################################################


#############################################################################################
# Début de la fonction crée le script de configuration du nombre d'éléments dans l'historique
#############################################################################################
	function creer_conf
	{
####### Début de la création du script nombre d'éléments ####################################
		mkdir /opt/Recents
		echo "#!/bin/bash
if [ -f /home/\$USER/.nombre-elements.txt ]
then
	maxHistory=\$(tail /home/\$USER/.nombre-elements.txt)
else
	maxHistory=10
fi
nombre=\$(whiptail --title \"Nombre d'éléments dans l'historique\" --inputbox \"Combien d'éléments voulez-vous dans l'historique?\" 8 78 \$maxHistory 3>&1 1>&2 2>&3)


if [[ \$nombre < \$maxHistory ]]
then
	for ((i=\$maxHistory; i>\$nombre; i--))
		do
			rm /home/\$USER/.local/share/applications/\$i-history.desktop
		done
fi
echo \$nombre > /home/\$USER/.nombre-elements.txt" > /opt/Recents/nombre-elements.sh


####### Fin de la création du script nombre d'éléments ######################################


####### Début de la création du raccourci nombre d'éléments #################################
		echo "[Desktop Entry]
Encoding=UTF-8
Name=Nombre d'éléments
Comment=Indiquer le nombre d'éléments à afficher dans l'historique
Exec=lxterminal --command=\"bash /opt/Recents/nombre-elements.sh\"
Icon=gnome-system
Type=Application
Categories=PreferencesHistorique;" > /usr/share/applications/nombre-elements.desktop
####### Fin de la création du raccourci nombre d'éléments ###################################
	}
#############################################################################################
# Fin de la fonction crée le script de configuration du nombre d'éléments dans l'historique #
#############################################################################################


#####################################################################################
# Début de la fonction crée le script de purge du nombre d'éléments dans l'historique
#####################################################################################
	function creer_clear
	{
####### Début de la création du script clear ########################################
		echo "#!/bin/bash
rm /home/\$USER/.local/share/applications/*-history.desktop" > /opt/Recents/clear-history.sh
####### Fin de la création du script clear ##########################################


####### Début de la création du raccourci clear #####################################
		echo "[Desktop Entry]
Encoding=UTF-8
Name=Vider l'historique
Comment=Vide la liste des fichiers récents
Exec=lxterminal --command=\"bash /opt/Recents/clear-history.sh\"
Icon=edit-delete
Type=Application
Categories=PreferencesHistorique;" > /usr/share/applications/clear-history.desktop
####### Fin de la création du raccourci clear #######################################
	}
#####################################################################################
# Fin de la fonction crée le script de purge du nombre d'éléments dans l'historique #
#####################################################################################


#####################################################
# Début de la fonction crée le script de l'historique
#####################################################
	function creer_historique
	{
		echo "#!/bin/bash


#################################################
# Début de déclaration des variables essentielles
#################################################
	dateReference=\$(date +%s)
	maxHistory=\"10\"
	
	if [ ! -d /home/\$USER/.local/share/applications ]
	then
		mkdir /home/\$USER/.local/share/applications
	fi


	if [ ! -f /home/\$USER/.log/historique.log ]
	then
		touch /home/\$USER/.log/historique.log
	else
		rm /home/\$USER/.log/historique.log
		touch /home/\$USER/.log/historique.log
	fi


	fileUsed=\"§\"
	fileName=\"§\"
#################################################
# Fin de déclaration des variables essentielles #
#################################################


#####################################################
# Début de la fonction de ré-encondage des caractères
#####################################################
	function reEncoding
	{
		fileUsed=\$(echo \$fileUsed | sed \"s/%20/ /g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%80/À/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%82/Â/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%84/Ä/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%88/È/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%89/É/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%8A/Ê/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%8B/Ë/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%8E/Î/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%8F/Ï/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%94/Ô/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%96/Ö/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%9B/Û/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%9C/Ü/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%A0/à/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%A2/â/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%A4/ä/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%A7/ç/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%A8/è/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%A9/é/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%AA/ê/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%AB/ë/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%AE/î/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%AF/ï/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%B4/ô/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%B6/ö/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%B9/ù/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%BB/û/g\")
		fileUsed=\$(echo \$fileUsed | sed \"s/%C3%BC/ü/g\")
	}
#####################################################
# Fin de la fonction de ré-encondage des caractères #
#####################################################


################################################
# Début de la fonction décalement des raccourcis
################################################
	function moveList
	{
		if [ -f /home/\$USER/.nombre-elements.txt ]
		then
			maxHistory=\$(tail /home/\$USER/.nombre-elements.txt)
		fi
		
		for ((i=\$maxHistory; i>1; i--))
		do
			j=\$((i-1))
			move=\$(mv /home/\$USER/.local/share/applications/\$j-history.desktop /home/\$USER/.local/share/applications/\$i-history.desktop)
		done
	}
################################################
# Fin de la fonction décalement des raccourcis #
################################################


#######################################################
# Début de la fonction d'écriture du raccourci numéro 1
#######################################################
	function createOne
	{
		if [ -f /home/\$USER/.local/share/applications/1-history.desktop ]
		then
			rm /home/\$USER/.local/share/applications/1-history.desktop
		fi
		
		touch /home/\$USER/.local/share/applications/1-history.desktop
		echo \"[Desktop Entry]
Name=\$fileName
Comment=\$fileUsed
Exec=\$applicationUsed \\\"\$fileUsed\\\"
Icon=\$iconUsed
Type=Application
Categories=Historique;\" > /home/\$USER/.local/share/applications/1-history.desktop
	}
#######################################################
# Fin de la fonction d'écriture du raccourci numéro 1 #
#######################################################


#############################################################
# Début de la fonction de traitement de l'historique de geany
#############################################################
	function recentlyGeany
	{
		fileUsed=\$(tail /home/\$USER/.config/geany/geany.conf | grep \"recent_files=\")


########### Début d'isolation du fichier modifié ############
		fileUsed=\$(echo \"\${fileUsed%%;*}\") # On supprime la fin
		fileUsed=\$(echo \$fileUsed | sed -e \"s/recent_files=//\")
		echo \"\$(date) -> recentlyGeany -> fileUsed -> \$fileUsed\" >> /home/\$USER/.log/historique.log
########### Fin d'isolation du fichier modifié ##############


		deja=\$(echo \"\$fileUsed\" | sed -r 's/(\[)/§/g')
		deja=\$(echo \"\$deja\" | sed -r 's/(\])/[[:print:]]/g')
		deja=\$(echo \"\$deja\" | sed -r 's/§/[[:print:]]/g')
		deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$deja\" | grep geany)
		echo \"\$(date) -> recentlyGeany -> deja -> \$deja\" >> /home/\$USER/.log/historique.log
		if [[ ! \$(echo \$deja) ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
		then
			echo \"\$(date) -> recentlyGeany -> PAS DE DOUBLON\" >> /home/\$USER/.log/historique.log
			fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
			iconUsed=\"geany\"
			applicationUsed=\"geany %u\"
			moveList
			createOne
		else
			echo \"\$(date) -> recentlyGeany -> UN DOUBLON\" >> /home/\$USER/.log/historique.log
		fi
		changed=1
	}
#############################################################
# Fin de la fonction de traitement de l'historique de geany #
#############################################################


###############################################################
# Début de la fonction de traitement de l'historique de abiword
###############################################################
	function recentlyAbiword
	{
		fileUsed=\$(cat /home/\$USER/.config/abiword/profile | grep \"name1=\")
		if [[ ! \$(echo \$fileUsed | grep \"\$fileName\") ]]
		then
########### Début d'isolation du fichier modifié ##############
			fileUsed=\$(echo \$fileUsed | sed -e \"s/\\\"//g\")
			fileUsed=\$(echo \$fileUsed | sed -e \"s/name1=file:\/\///\")
			echo \"\$(date) -> recentlyAbiword -> fileUsed -> \$fileUsed\" >> /home/\$USER/.log/historique.log
########### Fin d'isolation du fichier modifié ################


			deja=\$(echo \"\$fileUsed\" | sed -r 's/(\[)/§/g')
			deja=\$(echo \"\$deja\" | sed -r 's/(\])/[[:print:]]/g')
			deja=\$(echo \"\$deja\" | sed -r 's/§/[[:print:]]/g')
			deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$deja\" | grep abiword)
			echo \"\$(date) -> recentlyAbiword -> deja -> \$deja\" >> /home/\$USER/.log/historique.log
			if [[ ! \$(echo \$deja) ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
			then
				echo \"\$(date) -> recentlyAbiword -> PAS DE DOUBLON\" >> /home/\$USER/.log/historique.log
				fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
				iconUsed=\"abiword\"
				applicationUsed=\"abiword %u\"
				moveList
				createOne
			else
				echo \"\$(date) -> recentlyAbiword -> UN DOUBLON\" >> /home/\$USER/.log/historique.log
			fi
		fi
		changed=1
	}
###############################################################
# Fin de la fonction de traitement de l'historique de abiword #
###############################################################


###############################################################
# Début de la fonction de traitement de l'historique de acrobat
###############################################################
	function recentlyAcrobat
	{
		fileUsed=\$(cat -v /home/\$USER/.adobe/Acrobat/9.0/Preferences/reader_prefs | grep \"/RecentFiles\")
		if [[ ! \$(echo \$fileUsed | grep \"\$fileName\") ]]
		then
########### Début d'isolation du fichier modifié ##############
			fileUsed=\$(echo \$fileUsed | sed -e \"s/.*[(]//\") # on élimine le début
			fileUsed=\$(echo \$fileUsed | sed -e \"s/[)]\]//\") # on élimine la fin
			echo \"\$(date) -> recentlyAcrobat -> fileUsed -> \$fileUsed\" >> /home/\$USER/.log/historique.log
########### Fin d'isolation du fichier modifié ################


			deja=\$(echo \"\$fileUsed\" | sed -r 's/(\[)/§/g')
			deja=\$(echo \"\$deja\" | sed -r 's/(\])/[[:print:]]/g')
			deja=\$(echo \"\$deja\" | sed -r 's/§/[[:print:]]/g')
			deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$deja\" | grep acroread)
			echo \"\$(date) -> recentlyAcrobat -> deja -> \$deja\" >> /home/\$USER/.log/historique.log
			if [[ ! \$(echo \$deja) ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
			then
				echo \"\$(date) -> recentlyAcrobat -> PAS DE DOUBLON\" >> /home/\$USER/.log/historique.log
				fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
				iconUsed=\"AdobeReader9\"
				applicationUsed=\"acroread\"
				moveList
				createOne
			else
				echo \"\$(date) -> recentlyAcrobat -> UN DOUBLON\" >> /home/\$USER/.log/historique.log
			fi
		fi
		changed=1
	}
###############################################################
# Fin de la fonction de traitement de l'historique de acrobat #
###############################################################


###################################################################
# Début de la fonction de traitement de l'historique de libreoffice
###################################################################
	function recentlyLibreoffice
	{
		fileUsed=\$(cat /home/\$USER/.config/libreoffice/4/user/registrymodifications.xcu | grep 'PickList' | grep 'oor:name=\"0\"')
		if [[ \$(echo \$fileUsed | grep \"file\") ]] # on vérifie si le grep retourne un champ vide
		then
			if [[ ! \$(echo \$fileUsed | grep \"\$fileName\") ]] # on évite le doublon en comparant avec l'entrée précédente
			then
############### Début d'isolation du fichier modifié ##############
				fileUsed=\$(echo \$fileUsed | sed -e \"s/.*file:\/\///\") # on élimine le début
				fileUsed=\$(echo \"\${fileUsed%%<*}\") # On supprime la fin
				reEncoding
				echo \"\$(date) -> recentlyLibreoffice -> fileUsed -> \$fileUsed\" >> /home/\$USER/.log/historique.log
############### Fin d'isolation du fichier modifié ################


				deja=\$(echo \"\$fileUsed\" | sed -r 's/(\[)/§/g')
				deja=\$(echo \"\$deja\" | sed -r 's/(\])/[[:print:]]/g')
				deja=\$(echo \"\$deja\" | sed -r 's/§/[[:print:]]/g')
				deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$deja\" | grep libreoffice)
				echo \"\$(date) -> recentlyLibreoffice -> deja -> \$deja\" >> /home/\$USER/.log/historique.log
				if [[ ! \$(echo \$deja) ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
				then
					echo \"\$(date) -> recentlyLibreoffice -> PAS DE DOUBLON\" >> /home/\$USER/.log/historique.log
					fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
					extension=\$(echo \$fileName | sed \"s/.*\.//\")


################### Début de définition des extensions ############
					if [[ \"\$extension\" = \"odt\" ]] || [[ \"\$extension\" = \"ott\" ]] || [[ \"\$extension\" = \"fodt\" ]] || [[ \"\$extension\" = \"uot\" ]] || [[ \"\$extension\" = \"doc\" ]] || [[ \"\$extension\" = \"docx\" ]] || [[ \"\$extension\" = \"dot\" ]] || [[ \"\$extension\" = \"rtf\" ]]
					then
						iconUsed=\"libreoffice-writer\"
						applicationUsed=\"libreoffice --writer %U\"
					elif [[ \"\$extension\" = \"odf\" ]] || [[ \"\$extension\" = \"mml\" ]]
					then
						iconUsed=\"libreoffice-math\"
						applicationUsed=\"libreoffice --math %U\"
					elif [[ \"\$extension\" = \"odp\" ]] || [[ \"\$extension\" = \"otp\" ]] || [[ \"\$extension\" = \"fodp\" ]] || [[ \"\$extension\" = \"uop\" ]] || [[ \"\$extension\" = \"ppt\" ]] || [[ \"\$extension\" = \"pptx\" ]] || [[ \"\$extension\" = \"ppsx\" ]] || [[ \"\$extension\" = \"potm\" ]] || [[ \"\$extension\" = \"pps\" ]] || [[ \"\$extension\" = \"pot\" ]]
					then
						iconUsed=\"libreoffice-impress\"
						applicationUsed=\"libreoffice --impress %U\"
					elif [[ \"\$extension\" = \"odg\" ]] || [[ \"\$extension\" = \"otg\" ]] || [[ \"\$extension\" = \"fodg\" ]]
					then
						iconUsed=\"libreoffice-draw\"
						applicationUsed=\"libreoffice --draw %U\"
					elif [[ \"\$extension\" = \"ods\" ]] || [[ \"\$extension\" = \"ots\" ]] || [[ \"\$extension\" = \"fods\" ]] || [[ \"\$extension\" = \"uos\" ]] || [[ \"\$extension\" = \"xlsx\" ]] || [[ \"\$extension\" = \"xls\" ]] || [[ \"\$extension\" = \"xlt\" ]] || [[ \"\$extension\" = \"csv\" ]]
					then
						iconUsed=\"libreoffice-calc\"
						applicationUsed=\"libreoffice --calc %U\"
					fi
################### Fin de définition des extensions ##############
					moveList
					createOne
				else
					echo \"\$(date) -> recentlyLibreoffice -> UN DOUBLON\" >> /home/\$USER/.log/historique.log
				fi
			fi
		fi
		changed=1
	}
###################################################################
# Fin de la fonction de traitement de l'historique de libreoffice #
###################################################################


###############################################################
# Début de la fonction de traitement de l'historique de blender
###############################################################
	function recentlyBlender
	{
		fileUsed=\$(head -1 /home/\$USER/.config/blender/2.74/config/recent-files.txt)
		echo \"\$(date) -> recentlyBlender -> fileUsed -> \$fileUsed\" >> /home/\$USER/.log/historique.log
		if [[ \$(echo \$fileUsed | grep \"/\") ]] # on vérifie si le grep retourne un champ vide
		then
			if [[ ! \$(echo \$fileUsed | grep \"\$fileName\") ]]
			then
				deja=\$(echo \"\$fileUsed\" | sed -r 's/(\[)/§/g')
				deja=\$(echo \"\$deja\" | sed -r 's/(\])/[[:print:]]/g')
				deja=\$(echo \"\$deja\" | sed -r 's/§/[[:print:]]/g')
				deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$deja\" | grep blender)
				echo \"\$(date) -> recentlyBlender -> deja -> \$deja\" >> /home/\$USER/.log/historique.log
				if [[ ! \$(echo \$deja) ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
				then
					echo \"\$(date) -> recentlyBlender -> PAS DE DOUBLON\" >> /home/\$USER/.log/historique.log
					fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
					iconUsed=\"blender\"
					applicationUsed=\"blender %f\"
					moveList
					createOne
				else
					echo \"\$(date) -> recentlyBlender -> UN DOUBLON\" >> /home/\$USER/.log/historique.log
				fi
			fi
		fi
		changed=1
	}
###############################################################
# Fin de la fonction de traitement de l'historique de blender #
###############################################################


#################################################################
# Début de la fonction de traitement de l'historique de darktable
#################################################################
	function recentlyDarktable
	{
####### Début de récupération de la date de modification ########
		toGrep=\$(date --date=\"1970-01-01 \$dateDarktable sec GMT\" \"+%Y:%m:%d %H:%M:%S\")
		toGrep=\"\${toGrep:0:18}\"
		echo \"\$(date) -> recentlyDarktable -> toGrep -> \$toGrep\" >> /home/\$USER/.log/historique.log
####### Fin de récupération de la date de modification ##########


####### Début de la récupération des données à traiter ##########
		fileUsed=\$(cat -v /home/\$USER/.config/darktable/library.db | grep \"\$toGrep\" | sed -e \"s/\^@//g\")
####### Fin de la récupération des données à traiter ############


		if [[ \$fileUsed ]] # on vérifie si le grep retourne un champ vide
		then


########### Début d'extraction du chemin du fichier ouvert ######
			fileUsed=\$(echo \$fileUsed | sed -e \"s/\$toGrep/§/\")
			position=\`expr index \"\$fileUsed\" §\`
			fileUsed=\${fileUsed:(\$position+1)} # on élimine le début
			fileUsed=\$(echo \$fileUsed | sed -e \"s/:/§/\")
			fileUsed=\$(echo \"\${fileUsed%%§*}\") # On supprime la fin
			lastFolder=\$(echo \$fileUsed | sed \"s/.*\///\")
			lastFolder=\${lastFolder:0:3} # on elimine la fin
			fileUsed=\$(echo \"\${fileUsed%/*}\")
			fileUsed=\$(find \"\$fileUsed\" -maxdepth 1 -name \$lastFolder*)
			echo \"\$(date) -> recentlyDarktable -> fileUsed -> \$fileUsed\" >> /home/\$USER/.log/historique.log
########### Fin d'extraction du chemin du fichier ouvert ########


			if [[ \$(echo \$fileUsed | grep \" \/\") ]] # Si il existe plusieurs dossiers ayant les mêmes 3 premières lettres
			then
############### Début d'extraction du dossier parent ############
				fileUsed=\$(echo \$fileUsed | sed -e \"s/ \//§/\")
				fileUsed=\$(echo \"\${fileUsed%%§*}\") # On supprime la fin
				echo \"\$(date) -> recentlyDarktable -> fileUsed -> \$fileUsed\" >> /home/\$USER/.log/historique.log
				fileUsed2=\$(echo \"\${fileUsed%/*}\")
				echo \"\$(date) -> recentlyDarktable -> fileUsed2 -> \$fileUsed2\" >> /home/\$USER/.log/historique.log
############### Fin d'extraction du dossier parent ##############
			else # sinon, il n'y a qu'un seul dossier avec le meme début de nom
				fileUsed=\$(find \"\$fileUsed\" -maxdepth 1 -name \"*.xmp\" -mmin -1)
				fileUsed=\$(echo \$fileUsed | sed -e \"s/ /%20/g\")
				fileUsed=\$(echo \$fileUsed | sed -e \"s/%20\// \//\")
				echo \"\$(date) -> recentlyDarktable -> fileUsed -> \$fileUsed\" >> /home/\$USER/.log/historique.log
				fileUsed2=\$(echo \$fileUsed)
				echo \"\$(date) -> recentlyDarktable -> fileUsed2 -> \$fileUsed2\" >> /home/\$USER/.log/historique.log
			fi


			for fileUsed in \$fileUsed2 # Pour chaque éléments séparés par un espace
			do
############### Début de finalisation du traitement #############
				fileUsed=\$(echo \$fileUsed | sed -e \"s/§/ /g\")
				fileUsed=\$(echo \$fileUsed | sed -e \"s/.xmp//g\")
				reEncoding
				echo \"\$(date) -> recentlyDarktable -> fileUsed -> \$fileUsed\" >> /home/\$USER/.log/historique.log
############### Fin de finalisation du traitement ###############


				deja=\$(echo \"\$fileUsed\" | sed -r 's/(\[)/§/g')
				deja=\$(echo \"\$deja\" | sed -r 's/(\])/[[:print:]]/g')
				deja=\$(echo \"\$deja\" | sed -r 's/§/[[:print:]]/g')
				deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$deja\" | grep darktable)
				echo \"\$(date) -> recentlyDarktable -> deja -> \$deja\" >> /home/\$USER/.log/historique.log
				if [[ ! \$(echo \$deja) ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
				then
################### Début de création du raccourci ##############
					echo \"\$(date) -> recentlyDarktable -> PAS DE DOUBLON\" >> /home/\$USER/.log/historique.log
					fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
					iconUsed=\"darktable\"
					applicationUsed=\"darktable %U\"
					moveList
					createOne
################### Fin de création du raccourci ################
				else
					echo \"\$(date) -> recentlyDarktable -> UN DOUBLON\" >> /home/\$USER/.log/historique.log
				fi
			done
		fi
		changed=1
	}
#################################################################
# Fin de la fonction de traitement de l'historique de darktable #
#################################################################


#################################################################
# Début de la fonction de traitement de l'historique de audacious
#################################################################
	function recentlyAudacious
	{
####### Début de la récupération des données à traiter ##########
		fileUsed=\$(cat /home/\$USER/.config/audacious/playlists/1000.audpl | grep \"uri=\")
####### Fin de la récupération des données à traiter ############


		if [[ \$(echo \$fileUsed | grep \"/\") ]] # on vérifie si le grep retourne un champ vide
		then


########### Début d'extraction du chemin du fichier ouvert ######
			fileUsed=\$(echo \$fileUsed | sed \"s/ uri=file:\/\//§/\")
			fileUsed=\$(echo \"\${fileUsed%%§*}\") # On supprime la fin
			fileUsed=\$(echo \$fileUsed | sed \"s/uri=file:\/\///\")
			reEncoding
			echo \"\$(date) -> recentlyAudacious -> fileUsed -> \$fileUsed\" >> /home/\$USER/.log/historique.log
########### Fin d'extraction du chemin du fichier ouvert ########


			deja=\$(echo \"\$fileUsed\" | sed -r 's/(\[)/§/g')
			deja=\$(echo \"\$deja\" | sed -r 's/(\])/[[:print:]]/g')
			deja=\$(echo \"\$deja\" | sed -r 's/§/[[:print:]]/g')
			deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$deja\" | grep audacious)
			echo \"\$(date) -> recentlyAudacious -> deja -> \$deja\" >> /home/\$USER/.log/historique.log
			if [[ ! \$(echo \$deja) ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
			then
################### Début de création du raccourci ##############
				echo \"\$(date) -> recentlyAudacious -> PAS DE DOUBLON\" >> /home/\$USER/.log/historique.log
				fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
				iconUsed=\"audacious\"
				applicationUsed=\"audacious %U\"
				moveList
				createOne
################### Fin de création du raccourci ################
			else
				echo \"\$(date) -> recentlyAudacious -> UN DOUBLON\" >> /home/\$USER/.log/historique.log
			fi
		fi
		changed=1
	}
#################################################################
# Fin de la fonction de traitement de l'historique de audacious #
#################################################################


################################################################
# Début de la fonction de traitement de l'historique de audacity
################################################################
	function recentlyAudacity
	{
		if [[ \$(ps -e | grep audacity) ]]
		then
########### Début du la récupération du repère #################
			fileUsed=\$(tail -1 /home/\$USER/.audacity-data/audacity.cfg)
			toGrep=\$(echo \$fileUsed | sed -e \"s/.*=//\") # on supprime le début
			toGrep=\$(echo \$toGrep | sed -e \"s/\//\\\\\\\\\//g\")
			echo \"\$(date) -> recentlyAudacity -> toGrep -> \$toGrep\" >> /home/\$USER/.log/historique.log
########### Fin du la récupération du repère ###################


		else


############### Début d'extraction du chemin du fichier ouvert #
				fileUsed=\$(cat -v /home/\$USER/.audacity-data/audacity.cfg)
				fileUsed=\$(echo \$fileUsed | sed -e \"s/.*\$toGrep //\") # on élimine le début
				echo \"\$(date) -> recentlyAudacity -> fileUsed -> \$fileUsed\" >> /home/\$USER/.log/historique.log
				fileUsed2=\$(echo \$fileUsed | sed -e \"s/ /%20/g\")
				fileUsed2=\$(echo \$fileUsed2 | sed -e \"s/%20file/ file/g\")
				echo \"\$(date) -> recentlyAudacity -> fileUsed2 -> \$fileUsed2\" >> /home/\$USER/.log/historique.log
############### Fin d'extraction du chemin du fichier ouvert ###


			for fileUsed in \$fileUsed2 # Pour chaque éléments séparés par un espace
			do
############### Début de finalisation du traitement #############
				fileUsed=\$(echo \$fileUsed | sed -e \"s/.*=//\")
				reEncoding
				echo \"\$(date) -> recentlyAudacity -> fileUsed -> \$fileUsed\" >> /home/\$USER/.log/historique.log
############### Fin de finalisation du traitement ###############


				deja=\$(echo \"\$fileUsed\" | sed -r 's/(\[)/§/g')
				deja=\$(echo \"\$deja\" | sed -r 's/(\])/[[:print:]]/g')
				deja=\$(echo \"\$deja\" | sed -r 's/§/[[:print:]]/g')
				deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$deja\" | grep audacity)
				echo \"\$(date) -> recentlyAudacity -> deja -> \$deja\" >> /home/\$USER/.log/historique.log
				if [[ ! \$(echo \$deja) ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
				then
################### Début de création du raccourci ##############
					echo \"\$(date) -> recentlyAudacity -> PAS DE DOUBLON\" >> /home/\$USER/.log/historique.log
					fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
					iconUsed=\"audacity\"
					applicationUsed=\"audacity %F\"
					moveList
					createOne
################### Fin de création du raccourci ################
				else
					echo \"\$(date) -> recentlyAudacity -> UN DOUBLON\" >> /home/\$USER/.log/historique.log
				fi
			done
		fi
		changed=1
	}
################################################################
# Fin de la fonction de traitement de l'historique de audacity #
################################################################


###########################################################
# Début de la fonction de traitement de l'historique de vlc
###########################################################
	function recentlyVlc
	{
####### Début de la récupération des données à traiter ####
		fileUsed=\$(cat /home/\$USER/.config/vlc/vlc-qt-interface.conf | grep \"list=\\\"file\")
		fileUsed=\$(echo \$fileUsed | sed \"s/\\\"//g\")
####### Fin de la récupération des données à traiter ######


		if [[ \$(echo \$fileUsed | grep \"/\") ]] # on vérifie si le grep retourne un champ vide
		then


########### Début d'extraction du chemin du fichier ouvert
			fileUsed=\$(echo \$fileUsed | sed \"s/list=file:\/\///\")
			fileUsed=\$(echo \$fileUsed | sed \"s/, file/§/\")
			fileUsed=\$(echo \"\${fileUsed%§*}\") # On supprime la fin
			reEncoding
			echo \"\$(date) -> recentlyVlc -> fileUsed -> \$fileUsed\" >> /home/\$USER/.log/historique.log
########### Fin d'extraction du chemin du fichier ouvert ##


			deja=\$(echo \"\$fileUsed\" | sed -r 's/(\[)/§/g')
			deja=\$(echo \"\$deja\" | sed -r 's/(\])/[[:print:]]/g')
			deja=\$(echo \"\$deja\" | sed -r 's/§/[[:print:]]/g')
			deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$deja\" | grep vlc)
			echo \"\$(date) -> recentlyVlc -> deja -> \$deja\" >> /home/\$USER/.log/historique.log
			if [[ ! \$(echo \$deja) ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
			then


################### Début de création du raccourci ########
				echo \"\$(date) -> recentlyVlc -> PAS DE DOUBLON\" >> /home/\$USER/.log/historique.log
				fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
				iconUsed=\"vlc\"
				applicationUsed=\"/usr/bin/vlc --started-from-file %U\"
				moveList
				createOne
################### Fin de création du raccourci ##########
			else
				echo \"\$(date) -> recentlyVlc -> UN DOUBLON\" >> /home/\$USER/.log/historique.log
			fi
		fi
		changed=1
	}
###########################################################
# Fin de la fonction de traitement de l'historique de vlc #
###########################################################


############################################################
# Début de la fonction de traitement de l'historique général
############################################################
	function recentlyUsedXbel
	{
####### Début d'extraction de la dernière entrée ###########
		dateGeneralHistory2=\$((\$dateGeneralHistory-20))


		for ((i=0; i<20; i++))
		do
			dateGeneralHistory2=\$((\$dateGeneralHistory2+1))
			toGrep=\$(date --date=\"1970-01-01 \$dateGeneralHistory2 sec\" +%Y-%m-%dT%H:%M:%S)
			if [[ \$(cat /home/\$USER/.local/share/recently-used.xbel | grep \$toGrep) ]]
			then
				toTreat=\$(cat /home/\$USER/.local/share/recently-used.xbel | grep \$toGrep)
				echo \"\$(date) -> recentlyUsedXbel -> toTreat -> \$toTreat\" >> /home/\$USER/.log/historique.log
			fi
		done
####### Fin d'extraction de la dernière entrée #############


		if [[ \"\$toTreat\" = *\"bookmark\"* ]]
		then
			if [[ ! \$(echo \$toTreat | grep \"soffice\") ]] && [[ ! \$(echo \$toTreat | grep \"audacity\") ]]  && [[ ! \$(echo \$toTreat | grep \"darktable\") ]] # Si on retrouve le contenu de fileUsed dans toTreat, cela signifie que l'entrée précédente est la meme. on évite le doublon && si fileUsed contient soffice, ne pas s'executer && si fileUsed contient audacity, ne pas s'executer && si fileUsed contient darktable, ne pas s'executer
			then
############### Début d'isolation du fichier modifié #######
				fileUsed=\$(echo \$toTreat | sed -e \"s/.*file:\/\///\") # on supprime le début
				fileUsed=\$(echo \"\${fileUsed%%\\\"*}\") # On supprime la fin
				reEncoding # remplacement des codes caractères spéciaux du chemin vers le fichier
				echo \"\$(date) -> recentlyUsedXbel -> fileUsed -> \$fileUsed\" >> /home/\$USER/.log/historique.log
				if [ ! -f \"\$fileUsed\" ]
				then
					fileUsed=\$(ls \$fileUsed.*)
					echo \"\$(date) -> recentlyUsedXbel -> fileUsed -> \$fileUsed\" >> /home/\$USER/.log/historique.log
				fi
############### Fin d'isolation du fichier modifié #########


				deja=\$(echo \"\$fileUsed\" | sed -r 's/(\[)/§/g')
				deja=\$(echo \"\$deja\" | sed -r 's/(\])/[[:print:]]/g')
				deja=\$(echo \"\$deja\" | sed -r 's/§/[[:print:]]/g')
				deja=\$(grep -rnw \"/home/\$USER/.local/share/applications/\" -e \"\$deja\")
				echo \"\$(date) -> recentlyUsedXbel -> deja -> \$deja\" >> /home/\$USER/.log/historique.log
				if [[ ! \$(echo \$deja) ]] # on évite le doublon en cherchant un raccourcis déja créé avec le meme nom de fichier
				then


################### Début d'extraction de la date modified #
					toTreat=\$(echo \$toTreat | sed -e \"s/.*modified=\\\"//\") # on supprime le début
					toTreat=\$(echo \"\${toTreat%%Z*}\") # On supprime la fin
					toTreat=\$(cat /home/\$USER/.local/share/recently-used.xbel | grep \$toTreat)
					echo \"\$(date) -> recentlyUsedXbel -> toTreat -> \$toTreat\" >> /home/\$USER/.log/historique.log
################### Fin d'extraction de la date modified ###


################### Début d'isolation de l'application utilisé
					applicationUsed=\$(echo \$toTreat | sed -e \"s/.*exec=\\\"&apos;//\") # on supprime le début
					applicationUsed=\$(echo \"\${applicationUsed%%&*}\") # On supprime la fin
					echo \"\$(date) -> recentlyUsedXbel -> applicationUsed -> \$applicationUsed\" >> /home/\$USER/.log/historique.log
################### Fin d'isolation de l'application utilisé


					if [[ \"\$applicationUsed\" = *\"gedit\"* ]]
					then
						iconUsed=\"accessories-text-editor\"
					else
						iconUsed=\$(echo \$applicationUsed | sed -e \"s/ %u//\")
					fi


					fileName=\$(echo \$fileUsed | sed \"s/.*\///\")
					moveList
					createOne
					echo \"\$(date) -> recentlyUsedXbel -> CREATION LISTE GENERALE\" >> /home/\$USER/.log/historique.log
				fi
			fi
		fi
		changed=1
	}
############################################################
# Fin de la fonction de traitement de l'historique général #
############################################################


#########################
# Début du script général
#########################
	while true
	do
		changed=0
		dateGeneralHistory=\$(stat -c %Y /home/\$USER/.local/share/recently-used.xbel)
		dateGeany=\$(stat -c %Y /home/\$USER/.config/geany/geany.conf)
		dateAbiword=\$(stat -c %Y /home/\$USER/.config/abiword/profile)
		dateAcrobat=\$(stat -c %Y /home/\$USER/.adobe/Acrobat/9.0/Preferences/reader_prefs)
		dateLibreoffice=\$(stat -c %Y /home/\$USER/.config/libreoffice/4/user/registrymodifications.xcu)
		if [[ -f /home/\$USER/.config/blender/2.74/config/recent-files.txt ]]
		then
			dateBlender=\$(stat -c %Y /home/\$USER/.config/blender/2.74/config/recent-files.txt)
		fi
		dateDarktable=\$(stat -c %Y /home/\$USER/.config/darktable/library.db)
		dateAudacious=\$(stat -c %Y /home/\$USER/.config/audacious/playlists/1000.audpl)
		dateAudacity=\$(stat -c %Y /home/\$USER/.audacity-data/audacity.cfg)
		dateVlc=\$(stat -c %Y /home/\$USER/.config/vlc/vlc-qt-interface.conf)


		if [[ \"\$dateGeany\" > \"\$dateReference\" ]]
		then
			recentlyGeany
		fi


		if [[ \"\$dateAbiword\" > \"\$dateReference\" ]]
		then
			recentlyAbiword
		fi


		if [[ \"\$dateAcrobat\" > \"\$dateReference\" ]]
		then
			recentlyAcrobat
		fi


		if [[ \"\$dateLibreoffice\" > \"\$dateReference\" ]]
		then
			recentlyLibreoffice
		fi


		if [[ \"\$dateBlender\" > \"\$dateReference\" ]]
		then
			recentlyBlender
		fi


		if [[ \"\$dateDarktable\" > \"\$dateReference\" ]]
		then
			recentlyDarktable
		fi


		if [[ \"\$dateAudacious\" > \"\$dateReference\" ]]
		then
			recentlyAudacious
		fi


		if [[ \"\$dateAudacity\" > \"\$dateReference\" ]]
		then
			recentlyAudacity
		fi


		if [[ \"\$dateVlc\" > \"\$dateReference\" ]]
		then
			recentlyVlc
		fi


		if [[ \"\$dateGeneralHistory\" > \"\$dateReference\" ]]
		then
			recentlyUsedXbel
		fi


		if [[ \$changed == 1 ]]
		then
			dateReference=\$(date +%s)
		fi
		sleep 0.5
	done
#########################
# Fin du script général #
#########################" > /opt/Recents/historique.sh


		echo "[Desktop Entry]
Name=Script historique
Comment=Script historique
Exec=bash /opt/Recents/historique.sh" > /etc/xdg/autostart/historique.desktop
	}
#####################################################
# Fin de la fonction crée le script de l'historique #
#####################################################


###################################
# Début d'execution du code général
###################################
	temp=$(whoami)
	if [[ "$temp" != "root" ]]
	then
		whiptail --title "sudoer" --msgbox "Le programme doit être exécuté avec les droits super-administrateur sudo" 8 78
	else
		if [ -f /usr/share/desktop-directories/historique.directory ]
		then
			whiptail --title "Supprimer?" --yesno "Voulez-vous supprimer l'historique du menu?" --yes-button "Oui" --no-button "Non" 8 78 3>&1 1>&2 2>&3
			if [[ "$?" == "0" ]]
			then
				cp /etc/xdg/lubuntu/menus/lxde-applications.menu.old /etc/xdg/lubuntu/menus/lxde-applications.menu
				rm /usr/share/desktop-directories/historique.directory
				rm /usr/share/desktop-directories/preferences-historique.directory
				rm -rf /opt/Recents/
				rm /usr/share/applications/nombre-elements.desktop
				rm /usr/share/applications/clear-history.desktop
				rm /etc/xdg/autostart/historique.desktop
			fi
		else
			creer_menu
			creer_conf
			creer_clear
			creer_historique
		fi
	fi
#################################
# Fin d'execution du code général
#################################

```

---

