#ubuntu setting
##Root
1. sudo su -
2. passwd
3. 사용할 root pw 를 입력

##network
1. Edit - Virtual Network Editor 에서 Subnetmask를 local lan 과 같게 맞춰준다. 
{tab} ex) 192.168.0.0
2. 공유기 관리 페이지에 가서 SSH에 사용할 PORT를 포트포워딩 해준다.
3. 네트워크가 되면 성공

##ssh port change
포트를 22에서 9000으로 변경한다.  
1. sudo vi /etc/ssh/sshd_config
```
Port 22
```

##방화벽 설정
1. $ sudo ufw allow 9000
2. $ sudo ufw allow ssh
이렇게해서도 해결이 안되면 방화벽을 내림...
3. $ sudo ufw disable

##apt server
1. $ sudo apt-get update 가 안먹힐 경우
2. $ cd /etc/apt/
3. $ sudo cp source.list source.list_bak
4. vi source.list
'''
0,$s/kr.archive.ubuntu.com/old-releases.ubuntu.com/g
:wq
'''
5. sudo apt-get update
