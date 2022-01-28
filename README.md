# -_get_repolink () {

    local regex

    regex='(https?)://github.com/.+/.+'

    if [[ $UPSTREAM_REPO == "seka -i ]]

    then

        echo "aHR0cHM6Ly9naXRodWIuY29tL0pNVEhPTi1BUi9KTS1USE9OL2FyY2hpdmUvbWFzdGVyLnppcA=" | base64 -d

    elif [[ $UPSTREAM_REPO == "seka -i" ]]

    then

        echo "aHR0cHM6Ly9naXRodWIuY29tL0pNVEhPTi1BUi9KTS1USE9OL2FyY2hpdmUvbWFzdGVyLnppcA=" | base64 -d

    elif [[ $UPSTREAM_REPO =~ $regex ]]

    then

        if [[ $UPSTREAM_REPO_BRANCH ]]

        then

            echo "${UPSTREAM_REPO}/archive/${UPSTREAM_REPO_BRANCH}.zip"

        else

            echo "${UPSTREAM_REPO}/archive/master.zip"

        fi

    else

        echo "aHR0cHM6Ly9naXRodWIuY29tL0pNVEhPTi1BUi9KTS1USE9OL2FyY2hpdmUvbWFzdGVyLnppcA=" | base64 -d

    fi

}

_setting_bot () {

    local zippath

    zippath="sekaBot.zip"

    echo "  يتم تحميل ملفات سورس شيكا ..."

    wget -q $(_get_repolink) -O "$zippath"

    echo "  فك بيانات السورس ..."

    harteh3mk=$(zipinfo -1 "$zippath" | grep -v "/.");

    unzip -qq "$zippath"

    echo "✓"

    echo "  يتم التفريغ.."

    rm -rf "$zippath"

    sleep 5

    cd $hareh3mk

    echo "   بدء بوت شيكا    "

    echo "

                       

╋╋╋╋╋┏┓┏┓

╋┏┳━━┫┗┫┗┳━┳━┳┓

┫┃┃┃┏┫┃┃╋┃┃┃┃

┏┛┣┻┻┻━┻┻┻━┻┻━┛|

<|||||||>

|           <مو ملفاتي>            | 

|<--------------------->

    "

    python3 ../setup/updater.py ../requirements.txt requirements.txt

    python3 -m userbot

}

_settin
