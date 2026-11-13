# 📚 Biblioteca «Loubna de Córdoba» · Infraestructura Contenedorizada

![ASIR](https://img.shields.io/badge/Ciclo-2º_ASIR-blue)
![Módulo](https://img.shields.io/badge/Módulo-0379_Proyecto_Intermodular-informational)
![Curso](https://img.shields.io/badge/Curso-2026--2027-success)
![Docker](https://img.shields.io/badge/Stack-Docker_%7C_Koha_%7C_MariaDB_%7C_LDAP_%7C_Nginx-2496ED)

> **Título del Proyecto:** Despliegue e Infraestructura Contenedorizada de Servicios Web y Base de Datos Resiliente para Gestión de la Biblioteca «Loubna de Córdoba»  
> **Centro Educativo:** Campus Digital FP  
> **Ciclo Formativo:** CFGS Administración de Sistemas Informáticos en Red (ASIR · Modalidad TEC)  
> **Tutora:** Marta Peribañez Vela  

---

## 📖 Descripción del Proyecto

Este repositorio aloja el código, los ficheros de despliegue, los scripts de automatización y la documentación técnica del **Proyecto Intermodular de 2º de ASIR**. 

El objetivo es dotar a la **Biblioteca «Loubna de Córdoba»** de Campus Digital FP de una plataforma integral, segura y de alta disponibilidad mediante contenedores **Docker**, integrando:
* **Gestión Bibliotecaria (Koha ILS):** Catálogo en línea (OPAC) y panel de administración de préstamos y lectores.
* **Base de Datos Resiliente (MariaDB / PostgreSQL):** Persistencia de datos, inicialización automatizada, gestión segura de credenciales (*Docker Secrets*), privilegios mínimos y sondas de salud (*healthchecks*).
* **Motor de Indexación (Elasticsearch):** Búsquedas rápidas sobre el fondo documental.
* **Identidad Unificada (OpenLDAP / Active Directory):** Autenticación centralizada para alumnado y personal docente.
* **Proxy Inverso y Seguridad (Nginx + SSL/TLS):** Aislamiento de redes internas (`frontend_net` / `backend_net`) y cifrado extremo a extremo.
* **Sostenibilidad y Digitalización:** Carné digital mediante código QR y reutilización de equipos en modo *Kiosk*.

---

## 👥 Equipo y Distribución de Roles

| Integrante | Rol Principal | Responsabilidades Clave |
| :--- | :--- | :--- |
| **Oriana Blanco** | Coordinación, Gestión, Requisitos y Documentación | Introducción y contexto, marco legal (RGPD/licencias), requisitos (`RF`/`RNF`), partes contratantes, presupuesto, manual de usuario, control de calidad de la memoria y seguimiento semanal (modalidad remota Mar–May 2027). |
| **Fidel Ramírez** | Arquitectura Técnica, Despliegue, Seguridad y Testing | Estado del arte, planificación (WBS/Gantt), diseño de red y datos, despliegue Docker y seguridad, copias de seguridad, análisis de riesgos, plan de pruebas y manual de instalación. |
---

## 🔗 Herramientas y Enlaces del Equipo

* **Tablero de Tareas (Kanban):** `[Pegar aquí enlace a GitHub Projects / Trello]`
* **Memoria Compartida (Word / Drive):** `[Pegar aquí enlace a carpeta compartida]`
* **Entrega Aula Virtual:** Moodle Campus Digital FP (`H<n>_<Equipo>_<Proyecto>`)

---

## 📂 Estructura del Repositorio

```text
proyecto-biblioteca-loubna-asir/
├── README.md                 # Presentación general, roles y guía rápida
├── docs/                     # Entregables por hito, bitácora, incidencias y manuales
│   ├── bitacora.md           # Registro fechado del trabajo individual y grupal
│   ├── incidencias.md        # Registro de problemas técnicos y resoluciones
│   └── investigacion-bd.md   # Estudio comparativo y pruebas del gestor de BD
├── docker/                   # Infraestructura como código
│   ├── docker-compose.yml    # Orquestación de servicios, redes y healthchecks
│   ├── .env.example          # Plantilla de variables de entorno (sin secretos)
│   ├── initdb/               # Scripts SQL de inicialización automática
│   └── nginx/                # Configuración del proxy inverso y certificados SSL
├── scripts/                  # Automatización y mantenimiento
│   ├── backup.sh             # Copias de seguridad lógicas en caliente
│   ├── restore.sh            # Procedimiento de restauración verificada
│   └── healthcheck_test.sh   # Batería de comprobaciones del sistema
└── diagramas/                # Topología de red, arquitectura Docker y modelo E-R
```

---

## 📅 Planificación e Hitos (Curso 2026–2027)

| Hito | Fase / Entregable | Fecha Límite | Estado |
| :--- | :--- | :---: | :---: |
| **H0** | Constitución del equipo, roles e idea inicial | `16/10/2026` | ✅ Completado |
| **H1** | Propuesta formal aprobada (Anteproyecto) | `23/10/2026` | ✅ Completado |
| **H2** | Análisis actual/futuro, estado del arte, requisitos, diseño y planificación | `27/11/2026` | 🔄 En curso |
| **H3** | Desarrollo del Producto Mínimo Viable (MVP) y versión Beta | `19/02/2027` | ⏳ Pendiente |
| **H4** | Despliegue final, *hardening*, pruebas y manuales | `07/05/2027` | ⏳ Pendiente |
| **H5** | Depósito final de memoria (PDF) y código | `21/05/2027 (14:00)` | ⏳ Pendiente |

---

## 🚀 Despliegue Rápido (Entorno de Laboratorio)

```bash
# 1. Clonar el repositorio
git clone [https://github.com/](https://github.com/)<usuario-o-org>/proyecto-biblioteca-loubna-asir.git
cd proyecto-biblioteca-loubna-asir/docker

# 2. Preparar variables de entorno y secretos locales
cp .env.example .env
mkdir -p secrets
echo "clave_segura_db" > secrets/db_password.txt
echo "clave_segura_web" > secrets/web_db_password.txt

# 3. Levantar la infraestructura en segundo plano
docker compose up -d

# 4. Verificar el estado de salud de los contenedores
docker compose ps
```

---

## 📜 Licencia

Proyecto desarrollado bajo principios de **Software Libre y Código Abierto** con fines educativos para **Campus Digital FP**.
