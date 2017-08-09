APACHE HTTP SERVER


Aprimoramentos do núcleo

MPMs de carga em tempo de execução
Múltiplos MPMs agora podem ser criados como módulos carregáveis em tempo de compilação. O MPM de escolha pode ser configurado em tempo de execução via LoadModulediretiva.
Evento MPM
O Event MPM não é mais experimental, mas agora é totalmente suportado.
Suporte assíncrono
Melhor suporte para leitura / gravação assíncrona para suporte de MPMs e plataformas.
Configuração LogLevel por módulo e por diretório
O LogLevelagora pode ser configurado por módulo e por diretório. Novos níveis trace1 de trace8foram adicionados acima do debugnível de log.
Seções de configuração por solicitação
<If>, <ElseIf>E as <Else> seções podem ser usadas para configurar a configuração com base em critérios por solicitação.
Analisador de expressão de propósito geral
Um novo analisador de expressão permite especificar condições complexas usando uma sintaxe comum em directivas como SetEnvIfExpr, RewriteCond, Header, <If>, e outros.
KeepAliveTimeout em milissegundos
Agora é possível especificar KeepAliveTimeoutem milissegundos.
Diretriz NameVirtualHost
Não é mais necessário e agora está obsoleto.
Substituir a Configuração
A nova AllowOverrideList diretiva permite um controle mais fino que as diretivas são permitidas nos .htaccessarquivos.
Variáveis ​​do arquivo de configuração
Agora é possível as Define variáveis ​​na configuração, permitindo uma representação mais clara se o mesmo valor for usado em muitos lugares na configuração.
Redução de uso de memória
Apesar de muitos novos recursos, 2.4.x tende a usar menos memória do que 2.2.x.
topo
Novos Módulos

mod_proxy_fcgi
Fastend do protocolo FastCGI para mod_proxy
mod_proxy_scgi
Protocolo de protocolo SCGI para mod_proxy
mod_proxy_express
Fornece proxies reversos de massa dinamicamente configurados para mod_proxy
mod_remoteip
Substitui o aparente endereço IP remoto e o nome do host para a solicitação com a lista de endereços IP apresentada por um proxies ou um balanceador de carga por meio dos cabeçalhos das solicitações.
mod_heartmonitor, mod_lbmethod_heartbeat
Permita mod_proxy_balancerbasear decisões de balanceamento de carga no número de conexões ativas nos servidores backend.
mod_proxy_html
Anteriormente, um módulo de terceiros, isso suporta a fixação de links HTML em uma situação de proxy reverso, onde o backend gera URLs que não são válidos para os clientes do proxy.
mod_sed
Uma substituição avançada de mod_substitute, permite editar o corpo de resposta com o poder total de sed.
mod_auth_form
Permite a autenticação baseada em formulários.
mod_session
Permite o uso do estado da sessão para clientes, usando armazenamento de cookies ou banco de dados.
mod_allowmethods
Novo módulo para restringir determinados métodos HTTP sem interferir com autenticação ou autorização.
mod_lua
Incorpora o idioma Lua em httpd, para funções de configuração e lógica de pequenas empresas. (Experimental)
mod_log_debug
Permite a adição de log de depuração personalizável em diferentes fases do processamento da solicitação.
mod_buffer
Fornece armazenamento em buffer das pilhas de filtro de entrada e saída
mod_data
Converta o corpo da resposta em um URL de dados RFC2397
mod_ratelimit
Fornece Limitação de Taxa de Banda Larga para Clientes
mod_request
Fornece filtros para lidar e disponibilizar os organismos de solicitação HTTP
mod_reflector
Fornece Reflexão de um corpo de solicitação como uma resposta através da pilha de filtro de saída.
mod_slotmem_shm
Fornece um provedor de memória compartilhada baseado em slots (ala o painel de avaliação).
mod_xml2enc
Anteriormente, um módulo de terceiros, isso aceita a internacionalização em módulos de filtro baseados em libxml2 (com reconhecimento de marcação).
mod_macro (Disponível desde 2.4.5)
Fornecer macros dentro dos arquivos de configuração.
mod_proxy_wstunnel (Disponível desde 2.4.5)
Apoio de túneis de conexão web.
mod_authnz_fcgi (Disponível desde 2.4.10)
Habilite aplicativos do autorizador FastCGI para autenticar e / ou autorizar clientes.
mod_http2 (Disponível desde 2,4.17)
Suporte para a camada de transporte HTTP / 2.
mod_proxy_hcheck (Disponível desde 2.4.21)
Apoie verificações de saúde dinâmicas independentes para servidores de backend de proxiy remotos.
topo
Melhorias de módulo

mod_ssl
mod_sslAgora pode ser configurado para usar um servidor OCSP para verificar o status de validação de um certificado de cliente. O respondedor padrão é configurável, juntamente com a decisão de preferir ou não o respondedor designado no próprio certificado do cliente.
mod_ssl Agora também suporta grampeamento OCSP, onde o servidor pro-ativamente obtém uma verificação OCSP de seu certificado e transmite isso ao cliente durante o aperto de mão.
mod_ssl Agora pode ser configurado para compartilhar dados de Sessão SSL entre servidores através do memcached
As chaves EC agora são suportadas, além de RSA e DSA.
Suporte para TLS-SRP (disponível em 2.4.4 e posterior).
mod_proxy
A ProxyPassdirectiva agora está configurada de forma otimizada dentro de um bloco Locationou LocationMatch, e oferece uma vantagem de desempenho significativa em relação à sintaxe tradicional de dois parâmetros quando presente em grandes números.
O endereço de origem usado para solicitações de proxy agora é configurável.
Suporte para sockets de domínio Unix para o backend (disponível em 2.4.7 e posterior).
mod_proxy_balancer
Mais mudanças de configuração de tempo de execução para BalancerMembers via balance-manager
BalancerMembers adicionais podem ser adicionados em tempo de execução via balance-manager
Configuração de tempo de execução de um subconjunto de parâmetros Balancer
BalancerMembers pode ser configurado para 'Drenar' para que eles respondam apenas a sessões adesivas existentes, permitindo que elas sejam aceitas graciosamente offline.
As configurações do balanceador podem ser persistentes após reiniciar.
mod_cache
O mod_cachefiltro CACHE pode ser opcionalmente inserido em um determinado ponto na cadeia do filtro para fornecer um controle fino sobre o armazenamento em cache.
mod_cache Agora pode armazenar em segredo solicitações HEAD.
Sempre que possível, as mod_cachediretrizes agora podem ser definidas por diretório, em vez de por servidor.
O URL base de URLs em cache pode ser personalizado, de modo que um conjunto de caches possa compartilhar o mesmo prefixo de URL do nó de extremidade.
mod_cache Agora é capaz de fornecer dados em cache obsoletos quando um backend não está disponível (erro 5xx).
mod_cache Agora pode inserir HIT / MISS / REVALIDATE em um cabeçalho X-Cache.
mod_include
Suporte para o atributo 'onerror' dentro de um elemento 'include', permitindo que um documento de erro seja exibido por erro em vez da string de erro padrão.
mod_cgi, mod_include, mod_isapi, ...
A tradução de cabeçalhos para variáveis ​​de ambiente é mais rigorosa do que antes para mitigar alguns ataques possíveis de cross-site-scripting via injeção de cabeçalho. Os cabeçalhos que contêm caracteres inválidos (incluindo sublinhados) agora são silenciosamente descartados. As variáveis ​​de ambiente no Apache têm algumas dicas sobre como trabalhar em torno de clientes legados quebrados que exigem esses cabeçalhos. (Isso afeta todos os módulos que usam essas variáveis ​​de ambiente.)
mod_authz_core Containers de lógica de autorização
A lógica de autorização avançada agora pode ser especificada usando a Requirediretiva e as diretrizes de contêiner relacionadas, como <RequireAll>.
mod_rewrite
mod_rewriteAdiciona o [QSD] (Query String Discard) e as [END]bandeiras para RewriteRulesimplificar cenários comuns de reescrita.
Adiciona a possibilidade de usar expressões booleanas complexas em RewriteCond.
Permite o uso de consultas SQL como RewriteMapfunções.
mod_ldap, mod_authnz_ldap
mod_authnz_ldap Adiciona suporte para grupos aninhados.
mod_ldapAcrescenta LDAPConnectionPoolTTL, LDAPTimeoute outras melhorias no tratamento de tempo limite. Isto é especialmente útil para configurações em que um firewall com estado destrói as conexões inativas para o servidor LDAP.
mod_ldapAdiciona LDAPLibraryDebuginformações de depuração de log fornecidas pelo kit de ferramentas LDAP usado.
mod_info
mod_info Agora pode despejar a configuração pré-analisada para stdout durante a inicialização do servidor.
mod_auth_basic
Novo mecanismo genérico para autenticação básica falsa (disponível em 2.4.5 e posterior).
topo
Aprimoramentos de programas

fcgistarter
Novo FastCGI daemon starter utility
htcacheclean
Os URL atualizados em cache agora podem ser listados, com metadados opcionais incluídos.
Permitir exclusão explícita de URLs em cache individuais do cache.
Os tamanhos de arquivo agora podem ser arredondados para o tamanho do bloco dado, tornando o tamanho do mapa de limites mais próximo do tamanho real no disco.
O tamanho do cache agora pode ser limitado pelo número de inodes, em vez de ser limitado pelo tamanho dos arquivos no disco.
rotatelogs
Agora, você pode criar um link para o arquivo de log atual.
Agora, pode invocar um script personalizado pós-rotação.
htpasswd, htdbm
Suporte para o algoritmo bcrypt (disponível em 2.4.4 e posterior).
topo
Documentação

Mod_rewrite
A mod_rewritedocumentação foi reorganizada e quase completamente reescrita, com foco em exemplos e uso comum, além de mostrar quando outras soluções são mais apropriadas. O Reescrever Guia é agora uma seção de alto nível com muito mais detalhes e melhor organização.
Mod_ssl
A mod_ssldocumentação foi grandemente aprimorada, com mais exemplos no nível de inicialização, além do foco anterior nos detalhes técnicos.
Guia de armazenamento em cache
O Guia de armazenamento em cache foi reescrito para distinguir adequadamente os recursos de cache RFC2616 HTTP / 1.1 fornecidos pelo cache de mod_cachechave / valor genérico fornecido pela interface socache , bem como para cobrir caches especializados fornecidos por mecanismos como mod_file_cache.
topo
Alterações do desenvolvedor de módulos

Check Configuration Hook Adicionado
Foi adicionado um novo gancho, check_configque é executado entre os ganchos pre_confige open_logs. Ele também é executado antes do test_configgancho quando a -topção é passada httpd. O check_configgancho permite aos módulos rever os valores interdependentes da diretiva de configuração e ajustá-los enquanto as mensagens ainda podem ser logadas no console. O usuário pode, portanto, ser alertado de problemas de configuração errada antes que a open_logsfunção de gancho do núcleo redirecione a saída do console para o log de erros.
Expression Parser Adicionado
Agora temos um analisador de expressão de propósito geral, cuja API está exposta em ap_expr.h . Isso é adaptado do analisador de expressão implementado anteriormente em mod_ssl.
Containers de lógica de autorização
Os módulos de autorização agora se registram como um provedor, via ap_register_auth_provider (), para suportar a lógica de autorização avançada, como <RequireAll>.
Interface de cache de objetos pequenos
O cabeçalho ap_socache.h expõe uma interface baseada em provedor para armazenamento em cache de pequenos objetos de dados, com base na implementação anterior do mod_sslcache da sessão. Os provedores que usam um buffer cíclico de memória compartilhada, arquivos dbm baseados no disco e um cache distribuído com memcache são atualmente suportados.
Cache Status Hook Adicionado
O mod_cachemódulo agora inclui um novo cache_statusgancho, que é chamado quando a decisão de cache é conhecida. É fornecida uma implementação padrão que adiciona um opcional X-Cachee um X-Cache-Detailcabeçalho à resposta.
A documentação do desenvolvedor contém uma lista detalhada de mudanças na API .



nginx 

Changes with nginx 1.13.4                                        08 Aug 2017

    *) Feature: the ngx_http_mirror_module.

    *) Bugfix: client connections might be dropped during configuration
       testing when using the "reuseport" parameter of the "listen"
       directive on Linux.

    *) Bugfix: request body might not be available in subrequests if it was
       saved to a file and proxying was used.

    *) Bugfix: cleaning cache based on the "max_size" parameter did not work
       on Windows.

    *) Bugfix: any shared memory allocation required 4096 bytes on Windows.

    *) Bugfix: nginx worker might be terminated abnormally when using the
       "zone" directive inside the "upstream" block on Windows.


Changes with nginx 1.13.3                                        11 Jul 2017

    *) Security: a specially crafted request might result in an integer
       overflow and incorrect processing of ranges in the range filter,
       potentially resulting in sensitive information leak (CVE-2017-7529).
       
       wordpress
       
  Informações de Instalação / Atualização
Para baixar o WordPress 4.8.1, atualize-se automaticamente no menu Painel> Atualizações na área de administração do seu site ou visite https://wordpress.org/download/release-archive/ .

Para instruções passo a passo sobre como instalar e atualizar o WordPress:

Atualizando o WordPress
Se você é novo no WordPress, recomendamos que você comece com o seguinte:

Novo para WordPress - Onde começar
Primeiros passos com WordPress ou atualização do WordPress Extended
Lições de WordPress

Resumo
Da publicação de versão do WordPress 4.8.1 : o WordPress 4.8.1 contém 29 reparos de manutenção e aprimoramentos para a série de lançamento 4.8, entre eles estão as correções para o widget rich Text e a introdução do widget HTML personalizado.

Administração

# 40982 - Configurações do Link: armadilha de teclado de campo de estrutura personalizada
Ferramentas de compilação / teste

# 41327 - Bump Akismet External - 4.9 Edition
Comentários

# 40975 - Botões de comentários 'Empty Spam' e 'Empty Trash' não exibidos no celular
Customizar

# 40978 - Passador de rodapé do painel do Customizer faltando
# 40981 - Personalizador: Menus: é muito fácil excluir por engano um menu porque o link "Excluir menu" eo botão "Adicionar itens" estão muito próximos
# 41158 - Aumentar o índice Z do tinymce
# 41410 - Definir `'filter' => 'content'` no conteúdo do starter" business info "widget
Incorpora

# 41019 - oEmbed: Atualize VideoPress oEmbed URL
# 41048 - `WP_oEmbed_Controller :: get_proxy_item ()` deve remover `_wpnonce` do cached` $ args`
# 41299 - o proxy OEmbed falha para encaminhar maxwidth e maxheight params
Geral

# 41056 - WP-API JS Client: as configurações estão registradas incorretamente como uma coleção
meios de comunicação

# 41231 - media-views.js: Não é possível ler .length de indefinido (this.controller. $ UploaderToggler.length)
API REST

# 38964 - Adicionar filtro para permitir a resposta de modificação * após * dados incorporados são adicionados
# 40886 - REST API: as solicitações PUT falham nos servidores Nginx quando os permalinks extravagantes não estão ativados
Taxonomia

# 41010 - wp_get_object_terms () retorna os termos duplicados se mais de uma taxonomia for dada em args
TinyMCE

# 41408 - TinyMCE: imagens com link e legenda aparecem "quebradas" quando selecionadas
Widgets

# 40907 - Apresentar widget dedicado para código HTML
# 40935 - O Facebook Video funciona na pré-visualização, mas não no tema
# 40951 - Novo Widget de Texto - Alternando entre Visual / Text Editor Strips Out Code
# 40960 - Widgets: o widget Texto deve respeitar a configuração "Desativar o editor visual ao escrever"
# 40972 - O editor TinyMCE no widget de texto não possui conteúdo RTL
# 40974 - widget de texto atualizado, não salve texto (ao usar colar)
# 40977 - Widgets: Parâmetro de consulta para 'loop' adicionado para vídeos externos não hospedados
# 40986 - Widgets: widget de texto e widgets de mídia não podem ser editados no modo de acessibilidade
# 41021 - O widget de texto não mostra o campo Título ou o editor TinyMCE
# 41361 - O widget de texto pode aumentar o erro de JS se a base de personalização estiver inserida na tela de administração de widgets
# 41386 - Text Widget - Wording - Legacy Mode 4.8.1 beta
# 41392 - Os estilos de tema para o widget de texto não se aplicam ao widget HTML personalizado
# 41394 - Widget de texto: Renomeie o modo legado para o modo visual e melhore back-compat para filtros de widget_text
Lista de arquivos revisados
Wp-admin / css / themes.css
Wp-admin / css / widgets.css
Wp-admin / includes / class-wp-comments-list-table.php
Wp-admin / includes / options.php
Wp-admin / js / customize-controls.js
Wp-admin / js / customize-nav-menus.js
Wp-admin / js / widgets / media-widgets.js
Wp-admin / js / widgets / text-widgets.js
Wp-includes / class-oembed.php
Wp-includes / class-wp-customize-widgets.php
Wp-includes / class-wp-editor.php
Wp-includes / class-wp-oembed-controller.php
Wp-includes / default-widgets.php
Wp-includes / js / media-views.js
Wp-includes / js / media / views / uploader / inline.js
Wp-includes / js / tinymce / plugins / wordpress / plugin.js
Wp-includes / js / tinymce / skins / wordpress / wp-content.css
Wp-includes / js / wp-api.js
Wp-includes / media.php
Wp-includes / rest-api.php
Wp-includes / rest-api / class-wp-rest-server.php
Wp-includes / script-loader.php
Wp-includes / taxonomy.php
Wp-includes / theme.php
Wp-includes / version.php
Wp-includes / widgets.php
Wp-includes / widgets / class-wp-widget-media-video.php
Wp-includes / widgets / class-wp-widget-media.php
Wp-includes / widgets / class-wp-widget-text.php
