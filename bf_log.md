# BrainFlow - Log de Desenvolvimento

## [2025-09-19 14:30] - Prompt 1: Contextualização e Análise de Requisitos
### Ações Realizadas:
- ✅ Análise completa dos requisitos do BrainFlow MVP
- ✅ Confirmação do entendimento das especificações técnicas
- ✅ Identificação das funcionalidades core obrigatórias
- ✅ Criação do arquivo de log de desenvolvimento (bf_log.md)

### Decisões Tomadas:
- **Stack Confirmado**: Django 4.2+ + PostgreSQL (Backend) / React 18+ + Tailwind CSS (Frontend)
- **Foco MVP**: Simplicidade e entrada rápida no mercado, sem over-engineering
- **Funcionalidades Core**: Login seguro, criação de mapas drag-and-drop, exportação múltipla, responsividade
- **Restrições Aceitas**: Apenas formas retangulares com bordas arredondadas, conectores simétricos
- **Controles Específicos**: TAB (subtópico), Enter (editar), Delete (remover), Ctrl+Z/Y (undo/redo), etc.

### Especificações Técnicas Confirmadas:
**Backend Requirements**:
- Django 4.2+ (LTS)
- Django REST Framework  
- PostgreSQL 14+
- Pillow (processamento de imagens)
- django-cors-headers
- djangorestframework-simplejwt (JWT auth)
- celery + redis (background jobs)
- python-decouple (environment variables)

**Frontend Requirements**:
- React 18+
- Tailwind CSS 3+
- Axios (HTTP client)
- React Router DOM
- Konva.js ou Fabric.js (canvas manipulation)
- jsPDF (PDF export)
- FileSaver.js (download files)

**Funcionalidades Específicas Confirmadas**:
- Tópico central obrigatório em todo mapa
- Hierarquia ilimitada de profundidade
- Animações suaves (balões como galhos de árvore)
- Navegação touchpad (dois dedos arrastar, pinça zoom)
- Auto-save a cada 30 segundos
- Formatos de exportação: PNG, JPG, JPEG, SVG (máx 10MB)
- Conectores simples e simétricos

### Arquivos/Componentes Criados ou Modificados:
- `bf_log.md` - Arquivo de log de desenvolvimento (CRIADO)

### Próximos Passos:
- Aguardando instruções específicas do Prompt 2
- Pronto para iniciar estruturação do projeto backend/frontend
- Consulta às documentações oficiais confirmada como obrigatória

### Comprometimento Anti-Alucinação:
- ✅ NÃO adicionarei funcionalidades não especificadas
- ✅ NÃO suggerirei melhorias não solicitadas  
- ✅ Usarei APENAS bibliotecas e APIs das documentações oficiais listadas
- ✅ Focarei EXCLUSIVAMENTE no MVP simples descrito
- ✅ Pedirei esclarecimentos se algo for ambíguo

---

## [2025-09-19 14:45] - Prompt 2: Arquitetura e Stack Tecnológico
### Decisões de Stack:
- **Frontend**: React 18+ + Vite + Tailwind CSS - Justificativa: Performance < 2s load, componentes reutilizáveis MVP, styling rápido sem CSS custom
- **Canvas Library**: Konva.js + react-konva - Justificativa: Performance superior para 1000+ nós, 60fps garantido, melhor memory management vs Fabric.js
- **Backend**: Django 4.2+ + DRF + PostgreSQL - Justificativa: Rapid MVP development, ORM robusto, REST API padronizada
- **State Management**: Context API + useState/useReducer - Justificativa: Simplicidade MVP, sem complexidade Redux desnecessária
- **Build Tool**: Vite - Justificativa: Build time otimizado para target < 2s load
- **Deploy**: Docker + docker-compose - Justificativa: Ambiente consistente, fácil setup development/production

### Arquitetura Definida:
**Backend Structure**:
- Apps: `authentication/` (JWT), `maps/` (CRUD mapas), `exports/` (Celery tasks)
- Models: User (Django), MindMap, Node (hierarquia), Connection (linhas)
- API: DRF ViewSets, JWT auth, auto-save endpoints, export background jobs

**Frontend Structure**:
- Components: `Canvas/` (Konva), `Auth/` (JWT), `UI/` (Tailwind), `Maps/` (CRUD)
- Contexts: AuthContext (JWT), MapContext (canvas state), UIContext (UI state)
- Services: Axios HTTP client, API integration, auto-save logic

**Performance Optimizations**:
- Konva.js para render otimizado de 1000+ nós
- Vite para build < 2s target
- Context API ao invés de Redux (simplicidade MVP)
- Auto-save throttled a 30s (conforme spec)

### Dependências Identificadas:
**Backend Core**:
- Django==4.2.7, djangorestframework==3.14.0, djangorestframework-simplejwt==5.3.0
- psycopg2-binary==2.9.7, django-cors-headers==4.3.1, Pillow==10.0.1
- celery==5.3.4, redis==5.0.1, python-decouple==3.8

**Frontend Core**:
- react^18.2.0, react-dom^18.2.0, react-router-dom^6.8.0, axios^1.6.0
- konva^9.2.0, react-konva^18.2.10, tailwindcss^3.3.0
- jspdf^2.5.1, file-saver^2.0.5, vite^4.3.0

### Arquivos Criados:
- `requirements.txt` - Dependências Python backend completas
- `package.json` - Dependências Node.js frontend completas  
- `docker-compose.yml` - Environment desenvolvimento com PostgreSQL + Redis
- `tailwind.config.js` - Config Tailwind com cores BrainFlow e animações

### Justificativas Técnicas (Baseadas nos Requisitos MVP):
1. **Konva.js vs Fabric.js**: Konva tem melhor performance para 1000+ elementos, rendering 60fps garantido
2. **Vite vs CRA**: Build time significativamente menor, target < 2s load time
3. **Context API vs Redux**: MVP simples não justifica complexidade Redux, Context suficiente
4. **PostgreSQL**: Requisito obrigatório, JSON fields para canvas_data flexível
5. **Celery + Redis**: Background exports (PDF/SVG) sem bloquear UI

### Próximos Passos:
- Implementação do design system base
- Setup inicial Django backend
- Configuração React frontend base
- Integração Docker environment

---