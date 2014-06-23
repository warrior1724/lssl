**LSSL - Linux Switch and Stream Laptop**
=============

O projeto busca reunir aplicativos, bibliotecas e informação para operação da mesa de corte Blackmagic ATEM TVS com o sistema operacional GNU/Linux. Especificamente, colocaremos em uso um Laptop (mínimo i5 e 4GB RAM) para capturar, gravar e re-estrimar o fluxo de vídeo gerado pela ATEM TVS, além de realizar operações simples e efetivas da placa e como dar "preview", cortar, aplicar Downstream key e controlar volume dos canais de áudio da mesma. A parte de "streaming" é realizada pelo framework *Gstreamer* e as funções de corte e controle são possibilitadas pela biblioteca  https://github.com/petersimonsson/libqatemcontrol recentemente incorporada pelo cliente oficial de CasparCG https://github.com/CasparCG/Client. Também utilizamos Puredata com os "externals" de osc (open sound control) de Mr Peach para interfaciar as operações e automações (se desejadas) com o cliente do CasparCG, além de extender o controle e comandos para hardwares externos e controladores midis por exemplo.


*The project aims to gather apps, libs and info for putting up a GNU/Linux based Laptop (minimum i5 and 4 GB RAM) for capturing, recording and Re-streaming the mpegts stream file from the modest Blackmagic ATEM TVS, as well as doing some simple and effective  operations (not all operations at the moment) like previewing, cutting, downstream keying and controlling audio channels. The streaming part of it is done by *Gstreamer* and the control functions of the hardware are based in  https://github.com/petersimonsson/libqatemcontrol  recently build into CasparCG client https://github.com/CasparCG/Client. We use also Puredata with Mr Peaches open sound control externals for interfacing with CasparCG client and extending the operation and automation (if desired) to it's almost limitless power (connecting midi controllers, external hardwares, creating macros and so forth).*


**Quebrando em pedaços**

As peças do quebra-cabeça são:

- bmd-tools: Biblioteca para captura do stream gerado pela ATEM TVS - https://github.com/fabled/bmd-tools - No sistema de teste as últimas versões do Fabled quebraram compatibilidade com o S.O, então neste repositório se encontra uma versão funcional do código-fonte para Debian Testing: Dependências libusb-1.0-dev e .exe  do driver para Windows para extração do Firmware (deve ser a mesma versão do Firmware da sua ATEM TVS, testado com versão 4.2 que pode ser baixada aqui http://bit.ly/1nXVf5B . Primeiro passo é extrair o Firmware do executável (copie o BMDStreamingServer.exe, da pasta "program files/Blackmagic" de uma instalação de Windows para a pasta "bmd-tools"):

> $ cd bmd-tools 

> $ ./bmd-extractfw < BMDStreamingServer.exe


- gstreamer (0.10)