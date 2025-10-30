-- NANANA HUB - ESP POR TEAM
-- Por: Sua Assistente

local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local CoreGui = game:GetService("CoreGui")
local LocalPlayer = Players.LocalPlayer

-- Sistema de KEY
local CORRECT_KEY = "NANANABETA1.0"
local KEY_VERIFIED = false
local ESP_ENABLED = false

-- Variáveis para ESP
local ESPBoxes = {}
local ESPLabels = {}

-- Criar a GUI principal
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = "NananaHub"
ScreenGui.Parent = CoreGui
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

-- Tela de KEY
local KeyFrame = Instance.new("Frame")
KeyFrame.Name = "KeyFrame"
KeyFrame.Size = UDim2.new(0, 400, 0, 200)
KeyFrame.Position = UDim2.new(0.5, -200, 0.5, -100)
KeyFrame.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
KeyFrame.BorderSizePixel = 0
KeyFrame.Parent = ScreenGui

local KeyTitle = Instance.new("TextLabel")
KeyTitle.Name = "KeyTitle"
KeyTitle.Size = UDim2.new(1, 0, 0, 40)
KeyTitle.Position = UDim2.new(0, 0, 0, 60)
KeyTitle.BackgroundTransparency = 1
KeyTitle.Text = "🍌 NANANA HUB 🍌"
KeyTitle.TextColor3 = Color3.fromRGB(255, 200, 0)
KeyTitle.TextSize = 20
KeyTitle.Font = Enum.Font.GothamBold
KeyTitle.Parent = KeyFrame

local KeySubtitle = Instance.new("TextLabel")
KeySubtitle.Name = "KeySubtitle"
KeySubtitle.Size = UDim2.new(1, 0, 0, 30)
KeySubtitle.Position = UDim2.new(0, 0, 0, 100)
KeySubtitle.BackgroundTransparency = 1
KeySubtitle.Text = "Digite a KEY de acesso:"
KeySubtitle.TextColor3 = Color3.fromRGB(255, 255, 255)
KeySubtitle.TextSize = 14
KeySubtitle.Font = Enum.Font.Gotham
KeySubtitle.Parent = KeyFrame

local KeyInput = Instance.new("TextBox")
KeyInput.Name = "KeyInput"
KeyInput.Size = UDim2.new(0, 300, 0, 35)
KeyInput.Position = UDim2.new(0.5, -150, 0, 130)
KeyInput.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
KeyInput.TextColor3 = Color3.fromRGB(255, 255, 255)
KeyInput.PlaceholderText = "Digite a KEY aqui..."
KeyInput.Text = ""
KeyInput.TextSize = 14
KeyInput.Font = Enum.Font.Gotham
KeyInput.Parent = KeyFrame

local VerifyKeyButton = Instance.new("TextButton")
VerifyKeyButton.Name = "VerifyKeyButton"
VerifyKeyButton.Size = UDim2.new(0, 120, 0, 35)
VerifyKeyButton.Position = UDim2.new(0.5, -60, 0, 175)
VerifyKeyButton.BackgroundColor3 = Color3.fromRGB(255, 180, 0)
VerifyKeyButton.Text = "VERIFICAR KEY"
VerifyKeyButton.TextColor3 = Color3.fromRGB(0, 0, 0)
VerifyKeyButton.TextSize = 14
VerifyKeyButton.Font = Enum.Font.GothamBold
VerifyKeyButton.Parent = KeyFrame

local KeyError = Instance.new("TextLabel")
KeyError.Name = "KeyError"
KeyError.Size = UDim2.new(1, 0, 0, 20)
KeyError.Position = UDim2.new(0, 0, 0, 215)
KeyError.BackgroundTransparency = 1
KeyError.Text = ""
KeyError.TextColor3 = Color3.fromRGB(255, 50, 50)
KeyError.TextSize = 12
KeyError.Font = Enum.Font.Gotham
KeyError.Visible = false
KeyError.Parent = KeyFrame

-- Frame principal
local MainFrame = Instance.new("Frame")
MainFrame.Name = "MainFrame"
MainFrame.Size = UDim2.new(0, 400, 0, 250)
MainFrame.Position = UDim2.new(0.5, -200, 0.5, -125)
MainFrame.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
MainFrame.BorderSizePixel = 0
MainFrame.Active = true
MainFrame.Draggable = true
MainFrame.Visible = false
MainFrame.Parent = ScreenGui

local TitleBar = Instance.new("Frame")
TitleBar.Name = "TitleBar"
TitleBar.Size = UDim2.new(1, 0, 0, 30)
TitleBar.BackgroundColor3 = Color3.fromRGB(255, 200, 0)
TitleBar.BorderSizePixel = 0
TitleBar.Parent = MainFrame

local TitleLabel = Instance.new("TextLabel")
TitleLabel.Name = "Title"
TitleLabel.Size = UDim2.new(0, 200, 1, 0)
TitleLabel.Position = UDim2.new(0.5, -100, 0, 0)
TitleLabel.BackgroundTransparency = 1
TitleLabel.Text = "🍌 NANANA HUB 🍌"
TitleLabel.TextColor3 = Color3.fromRGB(0, 0, 0)
TitleLabel.TextSize = 16
TitleLabel.Font = Enum.Font.GothamBold
TitleLabel.Parent = TitleBar

-- Botão minimizar
local MinimizeButton = Instance.new("TextButton")
MinimizeButton.Name = "MinimizeButton"
MinimizeButton.Size = UDim2.new(0, 30, 1, 0)
MinimizeButton.Position = UDim2.new(1, -60, 0, 0)
MinimizeButton.BackgroundColor3 = Color3.fromRGB(255, 180, 0)
MinimizeButton.Text = "_"
MinimizeButton.TextColor3 = Color3.fromRGB(255, 255, 255)
MinimizeButton.TextSize = 14
MinimizeButton.Font = Enum.Font.GothamBold
MinimizeButton.Parent = TitleBar

-- Botão fechar
local CloseButton = Instance.new("TextButton")
CloseButton.Name = "CloseButton"
CloseButton.Size = UDim2.new(0, 30, 1, 0)
CloseButton.Position = UDim2.new(1, -30, 0, 0)
CloseButton.BackgroundColor3 = Color3.fromRGB(255, 80, 80)
CloseButton.Text = "X"
CloseButton.TextColor3 = Color3.fromRGB(255, 255, 255)
CloseButton.TextSize = 14
CloseButton.Font = Enum.Font.GothamBold
CloseButton.Parent = TitleBar

local ContentFrame = Instance.new("Frame")
ContentFrame.Name = "Content"
ContentFrame.Size = UDim2.new(1, -20, 1, -40)
ContentFrame.Position = UDim2.new(0, 10, 0, 40)
ContentFrame.BackgroundTransparency = 1
ContentFrame.Parent = MainFrame

local ESPButton = Instance.new("TextButton")
ESPButton.Name = "ESPButton"
ESPButton.Size = UDim2.new(1, 0, 0, 40)
ESPButton.Position = UDim2.new(0, 0, 0, 10)
ESPButton.BackgroundColor3 = Color3.fromRGB(255, 180, 0)
ESPButton.Text = "ATIVAR ESP"
ESPButton.TextColor3 = Color3.fromRGB(0, 0, 0)
ESPButton.TextSize = 14
ESPButton.Font = Enum.Font.GothamBold
ESPButton.Parent = ContentFrame

local StatusLabel = Instance.new("TextLabel")
StatusLabel.Name = "StatusLabel"
StatusLabel.Size = UDim2.new(1, 0, 0, 80)
StatusLabel.Position = UDim2.new(0, 0, 0, 60)
StatusLabel.BackgroundTransparency = 1
StatusLabel.Text = "Status: ESP Desativado\n\nVerde = Sobrevivente\nVermelho = Assassino\nAzul = Seu Time"
StatusLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
StatusLabel.TextSize = 12
StatusLabel.Font = Enum.Font.Gotham
StatusLabel.TextWrapped = true
StatusLabel.Parent = ContentFrame

-- Função para verificar KEY
local function VerifyKey()
    local inputKey = string.upper(KeyInput.Text)
    
    if inputKey == CORRECT_KEY then
        KEY_VERIFIED = true
        KeyFrame.Visible = false
        MainFrame.Visible = true
        KeyError.Visible = false
    else
        KeyError.Text = "KEY incorreta! Tente novamente."
        KeyError.Visible = true
        KeyInput.Text = ""
    end
end

-- Sistema de detecção por TEAM
local function GetPlayerRole(player)
    if not player or not player.Character then
        return "Desconhecido"
    end
    
    -- Método 1: Verificar pelo Team do Roblox
    if player.Team then
        local teamName = string.lower(player.Team.Name)
        if string.find(teamName, "assassin") or 
           string.find(teamName, "killer") or 
           string.find(teamName, "murder") or
           string.find(teamName, "matador") then
            return "Assassino"
        elseif string.find(teamName, "surviv") or 
               string.find(teamName, "sobreviv") or
               string.find(teamName, "innocent") then
            return "Sobrevivente"
        end
    end
    
    -- Método 2: Verificar por valores no player
    local roleValue = player:FindFirstChild("Role") or 
                     player:FindFirstChild("Team") or 
                     player:FindFirstChild("Status")
    
    if roleValue and (roleValue:IsA("StringValue") or roleValue:IsA("IntValue")) then
        local roleText = string.lower(tostring(roleValue.Value))
        if string.find(roleText, "assassin") or 
           string.find(roleText, "killer") or 
           string.find(roleText, "murder") then
            return "Assassino"
        elseif string.find(roleText, "surviv") or 
               string.find(roleText, "innocent") or
               string.find(roleText, "civilian") then
            return "Sobrevivente"
        end
    end
    
    -- Método 3: Verificar por ferramentas
    local character = player.Character
    for _, tool in pairs(character:GetChildren()) do
        if tool:IsA("Tool") then
            local toolName = string.lower(tool.Name)
            if string.find(toolName, "knife") or 
               string.find(toolName, "faca") or 
               string.find(toolName, "dagger") or
               string.find(toolName, "shank") then
                return "Assassino"
            end
        end
    end
    
    -- Método 4: Verificar backpack
    local backpack = player:FindFirstChild("Backpack")
    if backpack then
        for _, tool in pairs(backpack:GetChildren()) do
            if tool:IsA("Tool") then
                local toolName = string.lower(tool.Name)
                if string.find(toolName, "knife") or 
                   string.find(toolName, "faca") or 
                   string.find(toolName, "dagger") then
                    return "Assassino"
                end
            end
        end
    end
    
    return "Sobrevivente" -- Padrão
end

-- Função ESP com detecção por team
local function CreateESP(player)
    if player == LocalPlayer then return end
    
    local character = player.Character
    if not character then return end
    
    local humanoid = character:FindFirstChild("Humanoid")
    local head = character:FindFirstChild("Head")
    
    if not head or not humanoid or humanoid.Health <= 0 then return end
    
    -- Remover ESP antigo se existir
    if ESPBoxes[player] then
        ESPBoxes[player]:Destroy()
        ESPBoxes[player] = nil
    end
    if ESPLabels[player] then
        ESPLabels[player]:Destroy()
        ESPLabels[player] = nil
    end
    
    -- Criar caixa do ESP
    local Box = Instance.new("BoxHandleAdornment")
    Box.Name = player.Name .. "_ESP"
    Box.Adornee = head
    Box.AlwaysOnTop = true
    Box.ZIndex = 5
    Box.Size = Vector3.new(4, 6, 4)
    Box.Transparency = 0.4
    
    -- Criar label com nome do jogador
    local NameLabel = Instance.new("BillboardGui")
    NameLabel.Name = player.Name .. "_NameLabel"
    NameLabel.Adornee = head
    NameLabel.Size = UDim2.new(0, 200, 0, 60)
    NameLabel.StudsOffset = Vector3.new(0, 3.5, 0)
    NameLabel.AlwaysOnTop = true
    NameLabel.MaxDistance = 500
    NameLabel.Enabled = true
    
    local NameText = Instance.new("TextLabel")
    NameText.Size = UDim2.new(1, 0, 0.4, 0)
    NameText.Position = UDim2.new(0, 0, 0, 0)
    NameText.BackgroundTransparency = 1
    NameText.Text = player.DisplayName
    NameText.TextColor3 = Color3.fromRGB(255, 255, 255)
    NameText.TextStrokeTransparency = 0
    NameText.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
    NameText.TextSize = 14
    NameText.Font = Enum.Font.GothamBold
    NameText.Parent = NameLabel
    
    local RoleText = Instance.new("TextLabel")
    RoleText.Size = UDim2.new(1, 0, 0.3, 0)
    RoleText.Position = UDim2.new(0, 0, 0.4, 0)
    RoleText.BackgroundTransparency = 1
    RoleText.TextSize = 12
    RoleText.Font = Enum.Font.GothamBold
    RoleText.TextStrokeTransparency = 0
    RoleText.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
    RoleText.Parent = NameLabel
    
    local TeamText = Instance.new("TextLabel")
    TeamText.Size = UDim2.new(1, 0, 0.3, 0)
    TeamText.Position = UDim2.new(0, 0, 0.7, 0)
    TeamText.BackgroundTransparency = 1
    TeamText.TextSize = 11
    TeamText.Font = Enum.Font.Gotham
    TeamText.TextStrokeTransparency = 0
    TeamText.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
    TeamText.Parent = NameLabel
    
    -- Detectar papel do jogador
    local playerRole = GetPlayerRole(player)
    local playerTeam = player.Team and player.Team.Name or "Sem Time"
    
    -- Definir cores baseado no papel e time
    if playerRole == "Assassino" then
        Box.Color3 = Color3.fromRGB(255, 0, 0) -- Vermelho
        RoleText.Text = "🔪 ASSASSINO"
        RoleText.TextColor3 = Color3.fromRGB(255, 0, 0)
    else
        Box.Color3 = Color3.fromRGB(0, 255, 0) -- Verde
        RoleText.Text = "👤 SOBREVIVENTE"
        RoleText.TextColor3 = Color3.fromRGB(0, 255, 0)
    end
    
    -- Verificar se é do mesmo time
    if LocalPlayer.Team and player.Team and LocalPlayer.Team == player.Team then
        Box.Color3 = Color3.fromRGB(0, 100, 255) -- Azul para mesmo time
        RoleText.TextColor3 = Color3.fromRGB(0, 100, 255)
    end
    
    TeamText.Text = "Time: " .. playerTeam
    TeamText.TextColor3 = Color3.fromRGB(255, 255, 255)
    
    Box.Parent = head
    NameLabel.Parent = head
    
    ESPBoxes[player] = Box
    ESPLabels[player] = NameLabel
end

local function RemoveESP(player)
    if ESPBoxes[player] then
        ESPBoxes[player]:Destroy()
        ESPBoxes[player] = nil
    end
    if ESPLabels[player] then
        ESPLabels[player]:Destroy()
        ESPLabels[player] = nil
    end
end

local function ClearAllESP()
    for player, _ in pairs(ESPBoxes) do
        RemoveESP(player)
    end
    ESPBoxes = {}
    ESPLabels = {}
end

local function UpdateAllESP()
    if not ESP_ENABLED then return end
    
    for _, player in pairs(Players:GetPlayers()) do
        if player ~= LocalPlayer then
            coroutine.wrap(function()
                CreateESP(player)
            end)()
        end
    end
end

-- Função principal do ESP
local function ToggleESP()
    if not KEY_VERIFIED then return end
    
    ESP_ENABLED = not ESP_ENABLED
    
    if ESP_ENABLED then
        ESPButton.BackgroundColor3 = Color3.fromRGB(50, 255, 50)
        ESPButton.Text = "DESATIVAR ESP"
        StatusLabel.Text = "Status: ESP ATIVADO\n\n🟢 Verde = Sobrevivente\n🔴 Vermelho = Assassino\n🔵 Azul = Seu Time"
        
        -- Criar ESP para todos os jogadores
        for _, player in pairs(Players:GetPlayers()) do
            if player ~= LocalPlayer then
                CreateESP(player)
            end
        end
        
        -- Monitorar novos jogadores
        Players.PlayerAdded:Connect(function(player)
            wait(3)
            if ESP_ENABLED then
                CreateESP(player)
            end
        end)
        
        -- Monitorar mudanças de time
        LocalPlayer:GetPropertyChangedSignal("Team"):Connect(function()
            if ESP_ENABLED then
                wait(1)
                UpdateAllESP()
            end
        end)
        
        -- Atualizar a cada 3 segundos
        coroutine.wrap(function()
            while ESP_ENABLED do
                UpdateAllESP()
                wait(3)
            end
        end)()
        
    else
        ESPButton.BackgroundColor3 = Color3.fromRGB(255, 180, 0)
        ESPButton.Text = "ATIVAR ESP"
        StatusLabel.Text = "Status: ESP Desativado\n\nVerde = Sobrevivente\nVermelho = Assassino\nAzul = Seu Time"
        ClearAllESP()
    end
end

-- Função minimizar
local function ToggleMinimize()
    ContentFrame.Visible = not ContentFrame.Visible
    if ContentFrame.Visible then
        MainFrame.Size = UDim2.new(0, 400, 0, 250)
        MinimizeButton.Text = "_"
    else
        MainFrame.Size = UDim2.new(0, 400, 0, 30)
        MinimizeButton.Text = "□"
    end
end

-- Conexões
VerifyKeyButton.MouseButton1Click:Connect(VerifyKey)

KeyInput.FocusLost:Connect(function(enterPressed)
    if enterPressed then
        VerifyKey()
    end
end)

ESPButton.MouseButton1Click:Connect(ToggleESP)
MinimizeButton.MouseButton1Click:Connect(ToggleMinimize)
CloseButton.MouseButton1Click:Connect(function()
    ClearAllESP()
    ScreenGui:Destroy()
end)

-- Efeitos hover
ESPButton.MouseEnter:Connect(function()
    if ESP_ENABLED then
        ESPButton.BackgroundColor3 = Color3.fromRGB(80, 255, 80)
    else
        ESPButton.BackgroundColor3 = Color3.fromRGB(255, 200, 100)
    end
end)

ESPButton.MouseLeave:Connect(function()
    if ESP_ENABLED then
        ESPButton.BackgroundColor3 = Color3.fromRGB(50, 255, 50)
    else
        ESPButton.BackgroundColor3 = Color3.fromRGB(255, 180, 0)
    end
end)

MinimizeButton.MouseEnter:Connect(function()
    MinimizeButton.BackgroundColor3 = Color3.fromRGB(255, 200, 100)
end)

MinimizeButton.MouseLeave:Connect(function()
    MinimizeButton.BackgroundColor3 = Color3.fromRGB(255, 180, 0)
end)

CloseButton.MouseEnter:Connect(function()
    CloseButton.BackgroundColor3 = Color3.fromRGB(255, 100, 100)
end)

CloseButton.MouseLeave:Connect(function()
    CloseButton.BackgroundColor3 = Color3.fromRGB(255, 80, 80)
end)

-- Inicializar mostrando a tela de KEY
KeyFrame.Visible = true
MainFrame.Visible = false

print("NANANA HUB CARREGADO!")
print("Use a KEY: NANANABETA1.0")
